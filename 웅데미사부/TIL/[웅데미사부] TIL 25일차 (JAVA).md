---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 25일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "264"
tistoryPostUrl: https://yanacoding.tistory.com/264
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바의 파일과 디렉토리
### 표준 입출력
|클래스 변수|입출력 스트림|설명|
|---|---|---|
|System.in|InputStream|콘솔로부터 데이터를 입력받음.|
|System.out|PrintStream|콘솔로 데이터를 출력함.|
|System.err|PrintStream|콘솔로 데이터를 출력함.|
참고 : 파일의 제거나 디렉터리에 관한 작업 등은 입출력 스트림을 통해서는 수행할 수 없음.
#### 표준 입출력의 대상 변경
|메소드|설명|
|---|---|
|static void setIn(InputStream in)|입력 스트림의 대상을 전달된 입력 스트림으로 변경함.|
|static void setOut(PrintStream out)|출력 스트림의 대상을 전달된 출력 스트림으로 변경함.|
|static void setErr(PrintStream err)|출력 스트림의 대상을 전달된 출력 스트림으로 변경함.|
### RandomAccessFile class
순차적인 접근이 아닌 임의의 지점에 접근하여 작업을 수행하고자 할 때 사용. 파일만을 대상으로 하며, 임의의 지점에서 입출력을 동시에 수행할 수 있음.
RandomAccessFile 클래스의 생성자에는 인수로 파일의 이름뿐만 아니라 파일 모드(파일의 사용 용도를 나타내는 문자열)까지 함께 전달해야함. 
#### 대표적인 파일 모드
|파일 모드|설명|
|---|---|
|"r"|파일을 오로지 읽는 것만 가능한 모드로 개방함.|
|"rw"|파일을 읽고 쓰는 것이 모두 가능한 모드로 개방함. 만약 파일이 없으면 새로운 파일을 생성함.|
##### getFilePointer()
파일 포인터의 현재 위치를 확인.
##### seek()
파일 포인터의 위치를 변경.

### File class
입출력 스트림을 통해서는 파일의 제거나 디렉터리에 관한 작업 등을 수행 할 수 없지만, File 클래스를 통해 처리할 수 있음.
#### File 클래스의 다양한 메서드
|메소드|설명|
|---|---|
|boolean canRead()|해당 파일이 읽을 수 있는 파일인지를 검사함.|
|boolean canWrite()|해당 파일이 쓸 수 있는 파일인지를 검사함.|
|boolean delete()|해당 파일 또는 디렉터리를 삭제함.|
|boolean exists()|해당 파일이 존재하는지를 검사함.|
|String getPath()|해당 파일의 경로명을 문자열로 반환함.|
|boolean isAbsolute()|해당 파일의 경로명이 절대 경로인지를 검사함.|
|boolean isDirectory()|해당 파일이 디렉터리인지를 검사함.|
|boolean isFile()|해당 파일이 파일인지를 검사함.|
|long length()|해당 파일의 크기를 반환함.|
|boolean mkdir()|지정된 경로에 디렉터리를 생성함.|
|boolean mkdirs()|지정된 경로에 디렉터리를 생성하며, 필요한 모든 상위 디렉터리도 생성함.|
|boolean renameTo(File dest)|해당 파일의 이름을 전달된 파일 이름으로 변경함.|
|boolean setExecutable(boolean executable)<br><br>boolean setReadable(boolean readable)<br><br>boolean setWritable(boolean writable)<br><br>boolean setReadOnly()|해당 파일의 속성을 변경함.|


---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 