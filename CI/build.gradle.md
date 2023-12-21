plugins {  
	id 'java'  
	id 'org.springframework.boot' version '3.2.0'  
	id 'io.spring.dependency-management' version '1.1.3'  
	id 'org.asciidoctor.jvm.convert' version '3.3.2'  
	id 'checkstyle'  
	id 'jacoco'  
	id "org.sonarqube" version "4.4.1.3373"  
}  
  
group = 'com.tf4'  
version = '0.0.1-SNAPSHOT'  
  
java {  
	sourceCompatibility = '17'  
}  
  
jacoco {  
	toolVersion = "0.8.8"  
}  
  
repositories {  
	mavenCentral()  
}  
  
configurations {  
	compileOnly {  
		extendsFrom annotationProcessor  
	}  
	asciidoctorExtensions  
}  
  
dependencies {  
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'  
	implementation 'org.springframework.boot:spring-boot-starter-data-redis'  
	implementation 'org.springframework.boot:spring-boot-starter-validation'  
	implementation 'org.springframework.boot:spring-boot-starter-web'  
	implementation 'org.hibernate.orm:hibernate-spatial'  
	implementation 'io.jsonwebtoken:jjwt:0.9.1'  
	implementation 'javax.xml.bind:jaxb-api:2.3.1'  
	annotationProcessor 'org.springframework.boot:spring-boot-configuration-processor'  
	compileOnly 'org.projectlombok:lombok'  
	runtimeOnly 'com.mysql:mysql-connector-j'  
	annotationProcessor 'org.projectlombok:lombok'  
	testImplementation 'org.springframework.boot:spring-boot-starter-test'  
	testImplementation 'org.springframework.restdocs:spring-restdocs-mockmvc'  
	// RestDocs  
	asciidoctorExtensions 'org.springframework.restdocs:spring-restdocs-asciidoctor'  
	testImplementation 'org.springframework.restdocs:spring-restdocs-mockmvc'  
	//QueryDsl  
	implementation 'com.querydsl:querydsl-jpa:5.0.0:jakarta'  
	annotationProcessor "com.querydsl:querydsl-apt:${dependencyManagement.importedProperties['querydsl.version']}:jakarta"  
	annotationProcessor "jakarta.annotation:jakarta.annotation-api"  
	annotationProcessor "jakarta.persistence:jakarta.persistence-api"  
	implementation 'com.querydsl:querydsl-spatial'  
}  
  
def querydslSrcDir = 'src/main/generated'  
clean {  
	delete file(querydslSrcDir)  
}  
tasks.withType(JavaCompile) {  
	options.generatedSourceOutputDirectory = file(querydslSrcDir)  
}  
  
ext {  
	set('snippetsDir', file("build/generated-snippets"))  
}  
  
tasks.named('test') {  
	outputs.dir snippetsDir  
	useJUnitPlatform()  
}  
  
tasks.named('asciidoctor') {  
	configurations 'asciidoctorExtensions'  
	sources {  
	include("**/index.adoc")  
}  
inputs.dir snippetsDir  
baseDirFollowsSourceFile()  
  
dependsOn test  
}  
  
asciidoctor.doFirst {  
	delete file('src/main/resources/static/docs')  
}  
  
task createDocs(type: Copy) {  
	dependsOn asciidoctor  
	from file("build/docs/asciidoc")  
	into file("src/main/resources/static/docs")  
}  
  
bootJar {  
	dependsOn asciidoctor  
	dependsOn createDocs  
	from("${asciidoctor.outputDir}") {  
		into 'static/docs'  
	}  
}  
  
checkstyle {  
	maxWarnings = 0  
	toolVersion = "10.4"  
	configFile = file("checkstyle/naver-checkstyle-rules.xml")  
	configProperties = ["suppressionFile": "checkstyle/naver-checkstyle-suppressions.xml"]  
	sourceSets = [sourceSets.main] // CompileQuerydsl 오류 해결  
}  
task testCoverage(type: Test) {  
	group 'verification'  
	description 'Runs the unit tests with coverage'  
	dependsOn(':test',  
	':jacocoTestReport',  
	':jacocoTestCoverageVerification')  
	tasks['jacocoTestReport'].mustRunAfter(tasks['test'])  
	tasks['jacocoTestCoverageVerification'].mustRunAfter(tasks['jacocoTestReport'])  
}  

==jacocoTestReport== {  
	reports {  
	xml.required = true  
	}  
	excludedClassFilesForReport(classDirectories)  
	==finalizedBy 'jacocoTestCoverageVerification'==
}  

==jacocoTestCoverageVerification== {  
	excludedClassFilesForReport(classDirectories)  
	violationRules {  
		rule {  
			limit {  
				minimum = ==0.80==  
			}  
		}  
		rule {  
			enabled = true  
			element = =='BUNDLE'==  //BUNDLE, CLASS, PACKAGE, SOURCEFILE, METHOD  
			limit {  
				counter = 'LINE'  
				value = 'COVEREDRATIO'  
				minimum = ==0.80==  
			}  
		```
```/*  
		// 브랜치 커버리지 - 80% : 적용할지 고민  
		limit {  
			counter = 'BRANCH'  
			value = 'COVEREDRATIO'  
			minimum = 0.80  
		}  
		// 라인수 제한(설정시 총 추가할 코드 라인을 제한 할 수 있음)  
		limit {  
			counter = 'LINE'  
			value = 'TOTALCOUNT'  
			maximum = 200  
		}  
		// "해당 룰 안에서만" 커버리지 체크를 제외할 클래스 추가하기  
		// 주의 : 패키지 + 클래스명 을 적어줘야함(경로가 아님)  
		excludes = [  
			'Q*.class',  
			//'*.test.*',  
		]  
		*/ ```
```
		}  
	}  
}  
sonar {  
	properties {  
		property "sonar.projectKey", "TF3-Project-PhotoSpot_photospot-be"  
		property "sonar.organization", "tf4project-f1bean-f2donghun-f3jaii-tjeegu-f4yana-photospot"  
		property "sonar.host.url", "https://sonarcloud.io"  
		property 'sonar.java.checkstyle.reportPaths', 'build/reports/checkstyle/main.xml'  
		property 'sonar.coverage.jacoco.xmlReportPaths', 'build/reports/jacoco/test/jacocoTestReport.xml'  
	}  
}  
// Jacoco test coverage 에서 제외할 항목 추가  
/* 주의 : 경로가 아닌 '패키지 + 파일명'으로 작성, */  
private ==excludedClassFilesForReport(classDirectories)== {  
	classDirectories.setFrom(  
		files(classDirectories.files.collect {  
			fileTree(dir: it, exclude: `[`  
				=="**/Q*",  ==
				=="**/*Request*",  ==
				=="**/*Response*",  ==
				=="**/*Application*"  ==
			`]`)  
		})  
	)  
}