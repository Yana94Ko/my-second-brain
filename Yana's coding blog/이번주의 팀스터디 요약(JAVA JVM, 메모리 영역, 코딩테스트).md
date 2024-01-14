---
tistoryBlogName: yanacoding
tistoryTitle: 이번주의 팀스터디 요약(JAVA JVM, 메모리 영역, 코딩테스트)
tistoryVisibility: "3"
tistoryCategory: "1197248"
tistorySkipModal: true
tistoryPostId: "255"
tistoryPostUrl: https://yanacoding.tistory.com/255
---
# 93.5조의 팀스터디 🥊

# 이번주의 팀스터디 플랫폼 - 칠판 & 프로그래머스 [코딩테스트 JAVA](https://school.programmers.co.kr/learn/challenges)
# 월요일 - JAVA JVM, 자바 컴파일 과정
- 컴파일 :  고급언어로 작성된 .java파일을 기계어인 byte code 즉, .class파일로 변환하는 과정
- 컴파일 과정
```
1. 프로그래머가 java언어로 소스코드를 작성
2. javac 컴파일러를 사용해 .java소스 파일을 컴파일하고, 바이트코드로 변환된 .class파일을 생성
3. 컴파일된 바이트코드인 .class파일을 클래스로더에 전달
4. 클래스 로더는 동적 로딩을 통해 필요한 클래스를 로딩 및 링크하여 런타임 데이터 영역인 jvm의 메모리에 올림
5. 실행엔진은 jvm 메모리에 올라온 바이트코드들을 인터프리터 방식 혹은 jit 컴파일러 방식으로 실행
```
![](https://i.imgur.com/J9wd2n4.png)
![](https://i.imgur.com/M2BNc6c.png)


---
# 화요일 - [K번째 수](https://school.programmers.co.kr/learn/courses/30/lessons/42748)
### 베니의 풀이
```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        // commands의 배열의 길이 만큼 출력할 answer 생성
        int[] answer = new int[commands.length];
        for (int c=0; c<commands.length; c++){
            // i, j, k 입력
            int i = commands[c][0]-1;
            int j = commands[c][1]-1;
            int k = commands[c][2]-1;

            // 각 command별로 필요한 만큼 ans배열 생성
            int[] ans = new int[j-i+1];

            // i ~ j만큼 array의 해당 값 ans에 입력
            for (int cc=i; cc<=j; cc++){
                ans[cc-i] = array[cc];
            }

            Arrays.sort(ans);
            answer[c] = ans[k];
        }
        return answer;
    }
}
```
### 휘성리의 풀이
```java
import java.util.*;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        
        for (int i = 0; i < answer.length; i++) {
            int start = commands[i][0] - 1;
            int end = commands[i][1] - 1;
            int k = commands[i][2] - 1;
            
            
            
            if (start == end) {
                answer[i] = array[start]; 
                continue;
            }
            
            int[] arr = new int[end - start + 1];
            int n = 0;
            
            for (int j = start; j <= end; j++) {
                arr[n] = array[j];
                n++;
            }
            
            Arrays.sort(arr);
            
            answer[i] = arr[k];
            
        }
        
        
        return answer;
    }
}
```
### 저스틴과 야나는 아팠어요 😢😢😢

---
# 수요일 - JVM 메모리 구조
![](https://i.imgur.com/34Xw8nJ.png)

## 담당 파트(무엇이든 물어보세요)
베니 : Method Area, Heap Area
휘성리 : Stack Area, PC register
저스틴 : Native Method Stack

---
# 목요일 - [가장 가까운 같은 글자](https://school.programmers.co.kr/learn/courses/30/lessons/142086)
### 베니의 풀이
```java
// 풀이 1
import java.util.HashMap;
class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];
        HashMap<Character, Integer> map = new HashMap<>();
        for (int i=0; i<s.length(); i++){
            char c = s.charAt(i);
            if (map.get(c) == null){
                answer[i] = -1;
            }else{
                answer[i] = i - map.get(c);
            }
            map.put(c, i);
        }

        return answer;
    }
}

// 풀이 2
import java.util.Arrays;
class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];
        int[] check = new int[26];
        Arrays.fill(check, -1);
        for (int i=0; i<s.length(); i++){
            int c = s.charAt(i)-'a';
            if (check[c] == -1)
                answer[i] = -1;
            else
                answer[i] = i - check[c];
            check[c] = i;
        }
        return answer;
    }
}
```
### 휘성리의 풀이
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] solution(String s) {
        int[] arr = new int[s.length()];

        Map<Character, Integer> hmap = new HashMap<>();

        for (int i = 0; i < s.length(); i++) {

            if (!hmap.containsKey(s.charAt(i))) {
                arr[i] = -1;
                hmap.put(s.charAt(i), i);
            } else {

                arr[i] = i - hmap.get(s.charAt(i));
                hmap.put(s.charAt(i), i);
            }
        }


        return arr;
    }
}
```
### 저스틴의 풀이
```java
import java.util.*;

class Solution {
    /*
    public int[] solution(String s) {
        int[] ans = new int[s.length()];
        Arrays.fill(ans, -1);

        char[] charArr = s.toCharArray();
        for (int i = 0; i < s.length(); i++) {
            char curChar = charArr[i];
            for (int j = i - 1; j >= 0; j--) {
                if (charArr[j] == charArr[i]) {
                    ans[i] = i - j;
                    break;
                }
            }
        }

        return ans;
    }
    */
    public int[] solution(String s) {

        HashMap<Character, Integer> map = new HashMap<>();
        char[] charArr = s.toCharArray();

        int[] ans = new int[s.length()];
        for (int i = 0; i < charArr.length; i++) {
            char cur = charArr[i];
            if (map.containsKey(cur)) {
                ans[i] = i - map.get(cur);
            }
            else {
                ans[i] = -1;
            }
            map.put(cur, i);
        }

        return ans;
    }
}
```
### 야나의 풀이
### 야나는 아팠어요 😢😢😢

---
# 금요일 [짝지어 제거하기](https://school.programmers.co.kr/learn/courses/30/lessons/12973?language=java)
### 베니의 풀이
```java
import java.util.Stack;
class Solution
{
    public int solution(String s)
    {
        int answer = 0;
        Stack<Character> str = new Stack<Character>();
        for(int i=0; i<s.length(); i++){
            char now = s.charAt(i);
            if (str.isEmpty())
                str.push(now);
            else{
                if (str.peek() == now)
                    str.pop();
                else
                    str.push(now);
            }
        }
        if (str.isEmpty())
            answer = 1;
        return answer;
    }
}
```
### 휘성리의 풀이
```java
import java.util.Stack;

class Solution {
    public int solution(String s) {
        char[] cArr = s.toCharArray();

        Stack<Character> stack = new Stack<>();


        for (int i = 0; i < cArr.length; i++) {
            char c = cArr[i];

            if (stack.isEmpty()) {
                stack.push(c);
            } else if (stack.peek() == c) {
                stack.pop();
            } else {
                stack.push(c);
            }


        }

        int answer = stack.size() == 0 ? 1 : 0;

        return answer;
    }
}
```
### 저스틴의 풀이
```java
import java.util.*;

class Solution {

    public int solution(String s) {
        char[] charArr = s.toCharArray();
        Stack<Character> st1 = new Stack<Character>();
        Stack<Character> st2 = new Stack<Character>();

        for (int i = charArr.length - 1; i >= 0; i--) {
            st1.push(charArr[i]);
        }

        while (!st1.empty()) {
            if (st2.empty() || st2.peek() != st1.peek()) {
                st2.push(st1.pop());
            }
            else if (st1.peek() == st2.peek()) {
                st1.pop();
                st2.pop();
            }
        }
        return st2.empty() ? 1 : 0;
    }
}
```
### 야나의 풀이(등장 🌟)
```java
import java.util.Stack;
class Solution{
    public int solution(String s){
        Stack<Character> st = new Stack<>(); 
        for(char c : s.toCharArray()){
            if(!st.isEmpty() && st.peek() == c){
                st.pop();
            }else{
                st.push(c);
            }
        }
        return st.isEmpty() ? 1 : 0;
    }
}
```

---
# 회고
 - 베니 : 
	 - 팀원들의 건강 문제로! 😷 이번주 출석률이 저조해 팀 분위기가 붕 떴던것 같습니다.(화요일 출석률 50%...! 😱) . 
	 - 모두 건강 조심하셔서 무사히 교육 마칠 수 있으면 좋겠습니다.
	 - 파이썬은 위대하다!!
 - 휘성리 : 
	 - 첫째날과 마지막날 빼고 다 같이 모이지를 못해서 계획대로 스터디를 진행하지 못한점은 아쉬우나 다들 건강하게 복귀해서 다행입니다 ! 😄 JVM에 대해서 조금 더 배우는 시간을 가질 수 있어서 좋았습니다! 코테도 답을 맞춘 후에 다양한 방법으로 풀어볼 수 있는 시간을 가져서 재미있었어요!
 - 저스틴 : 
	 - JVM의 메모리 구조에 관한 전반적인 큰 그림을 볼 수 있어 좋았다. 추후 더 자세히 공부하고 정리하는 과정은 필수적일듯!
	 - 코테 문제를 풀 때, 풀이에 적절한 자료구조(스택 등)를 빠르게 캐치해내는 능력의 중요성을 새삼 다시 한번 체감하였음
 - 야나 : 
	 - 코로나....살려주세요... 🏥🏥🏥 다들 건강합시다...
	 - JAVA의 JVM에 대해서 거의 2년만에 다시 공부하게 되어 좋았어요...
	 - GC를 다루지 못해 아쉽지만, 백엔드 스터디에서 다룰거니까 기대하세요..?
	 - 코테 푸는건 항상 즐거워 🎵