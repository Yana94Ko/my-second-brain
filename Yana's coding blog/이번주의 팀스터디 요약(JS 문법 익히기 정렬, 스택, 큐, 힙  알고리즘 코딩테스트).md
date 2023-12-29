---
tistoryBlogName: yanacoding
tistoryTitle: 이번주의 팀스터디 요약(JS 문법 익히기 정렬, 스택, 큐, 힙  알고리즘 코딩테스트)
tistoryTags: Js,Javascript,스택,큐,힙,heap,stack,queue
tistoryVisibility: "3"
tistoryCategory: "1197248"
tistorySkipModal: true
tistoryPostId: "235"
tistoryPostUrl: https://yanacoding.tistory.com/235
---
# T1F3조의 팀스터디 🥊

# 이번주의 팀스터디 플랫폼 - 프로그래머스 [코딩테스트 고득점 Kit](https://school.programmers.co.kr/learn/challenges?tab=algorithm_practice_kit)

---
# 월요일 : 🎄 즐거웠던 크리스마스 🎄

---
# 화요일 : 정렬, 큐 문제 풀이 | 수요일 : 발표
## 1. [K번째 수(정렬)](https://school.programmers.co.kr/learn/courses/30/lessons/42748)
### 유키의 풀이
```js
function solution(array, commands) {
    let result=[]
    commands.map((arr,i)=>{
        result.push(array.slice(arr[0]-1,arr[1]).sort((a,b)=>a-b)[arr[2]-1])})

    return result
}
```
### MZ의 풀이
```js
function solution(array, commands) {
    const answer = [];
    
    for (const command of commands) {
        const [i, j, k] = command;
        const sliceArray = array.slice(i-1, j);
        const sortedArray = sliceArray.sort((a,b) => a - b);
        answer.push(sortedArray[k-1]);
    }
    return answer;
}
```
### BASH의 풀이(파이썬)
```python
function solution(s) {
    answer = true;
    stack = [];
    
    for (let x of s) {
        if (x === '(') {
            stack.push(x);
        } else if (x === ')') {
            // 스택에 아이템이 있으면 팝
            if (stack.length) {
                stack.pop();
            } else {
                return false;
            }
        }
    }
    
    // 문자열을 다 탐색한 후에 stack에 문자가 남아있으면 false
    if (stack.length) {
        answer = false;
    }

    return answer;
```
### 야나의 풀이
```js
function solution(array, commands) {
    var answer = [];
    for(const command of commands){
        answer.push(
            array
                .slice(command[0]-1,command[1])
                .sort((a, b) => a - b)[command[2]-1]
                   )
    }
    return answer;
}
```
## 2. [가장 큰 수(정렬)](https://school.programmers.co.kr/learn/courses/30/lessons/42746)
### 유키의 풀이
```js
function solution(numbers) {
    var answer=''
    answer=numbers.map(number=>String(number)).sort((a,b)=>(b+a)-(a+b)).join('')

    return answer[0]==='0'?'0':answer;
}
```
### MZ의 풀이
```js
function solution(numbers) {
    const answer = numbers.map(num => num.toString())
    .sort((a, b) => (b + a) - (a + b))
    .join('');

    // 모든 숫자가 0인 경우 예외 처리
    if (answer[0] === '0') {
        return '0';
    }

    return answer;
}
```
### BASH의 풀이
```js
function solution(numbers) {
    var answer = '';
    
    stringArr = numbers.map(item => String(item));
    answer = stringArr.sort((a, b) => (b + a) - (a + b)).join('');
    
    return answer[0] === "0" ? "0" : answer;
}
```
### 야나의 풀이
```js
function solution(numbers) {
    const str = numbers
        .map(String)
        .sort((a,b) => (b + a) - (a + b))
        .join("");
    
    return str.charAt(0) =="0" ? "0" : str;
}
```
## 3. [H-index(정렬)](https://school.programmers.co.kr/learn/courses/30/lessons/42747)
### 유키의 풀이
```js
function solution(citations) {
    let i=0;
    
    citations.sort((a,b)=>b-a);
    
    while(citations[i]>=i+1){
        i++;
    }
    return i
    
}
```
### MZ의 풀이
```
60일 뒤에 공개됩니다
```
### BASH의 풀이
```python
def solution(citations):
    answer = 0
    n = len(citations)
    
    citations.sort(reverse=True);
    
    for i in range(n):
        if i >= citations[i]:
            return i
    
    # h번 이상 인용된 논문이 h편이상, 나머지가 h번 이하 인용
    
    # citations 발표한 논문의 인용횟수 들이 담긴 배열
    # len(citations) 발표 논문 수
    
    return n
```
### 야나의 풀이
```js
function solution(citations) {
    //내림차순 정렬
    citations.sort((a,b) => b - a);
    console.log(citations)
    // [0] [0,0,0,0...] => 0 예외 발생
    if(citations.every(element => element === 0)){
        return 0;
    }
    for(let i = 1; i < citations.length; i++){
        // idx 0인 경우 무조건 fail -> 다음 순서로 넘어가 비교한뒤, idx가 해당 idx의 value보다 크거나 같아진 경우 반환
        if(i >= citations[i]){
            return i;
        }
    }
    // for(let i = 0; i < citations.length; i++){
    //     // idx 0인 경우 무조건 fail -> 다음 순서로 넘어가 비교한뒤, idx가 해당 idx의 value보다 크거나 같아진 경우 반환
    //     if(i >= citations[i]){
    //         return i;
    //     }
    // }
    return citations.length;
}
```

## 4. [프로세스(Queue)](https://school.programmers.co.kr/learn/courses/30/lessons/42587)
### 유키의 풀이
```js
function solution(priorities, location) {
    var answer = 0;
    const idxArr=Array(priorities.length).fill(0).map((v,i)=>i);
    let max=Math.max(...priorities)
    
    while(priorities.length!=0){
        
        //뒤로 가서 다시 줄서기 (우선순위 불충족)
        if(priorities[0]<max){
            priorities.push(priorities.shift());
            idxArr.push(idxArr.shift()); 
        }
        //큐에서 탈출 (우선순위 충족)
        else {
            priorities.shift();
            answer++;
            max=Math.max(...priorities);
            
            //location 확인
            if(idxArr.shift()===location){
                return answer;
            }
            
        }
    }
    
    
    
    }
```
### MZ의 풀이
```js
function solution(priorities, location) {
    const queue = priorities.map((priority, index) => ({priority, index}));
    let answer = 0;
    
    while (queue.length > 0) {
        const currentProcess = queue.shift();
        const isHigherPriority = queue.some(process => process.priority > currentProcess.priority);
        
        if (isHigherPriority) {
            queue.push(currentProcess);
        } else {
            answer++;
            if (currentProcess.index === location) {
                return answer;
            }
        }
    }
        
    return -1;
}
```
### BASH의 풀이
```python
from collections import deque

def solution(priorities, location):
    answer = 0
    queue = deque([(priority, key) for (key, priority) in enumerate(priorities)])   # 우선순위값과 프로세스번호(인덱스)를 튜플로 묶어 큐에 삽입.
 
    while queue:
        curPriority, curKey = queue.popleft()   # (우선순위, 프로세스번호)를 pop함.
        # cur와 배열안의 나머지숫자들과 비교.
        if all(curPriority >= item for (item, key) in queue):
            answer += 1
            # 알고싶은 위치의 프로세스 넘버라면 return.
            if curKey == location:
                return answer
        else:
            queue.append((curPriority, curKey))
```
### 야나의 풀이
```js
class Queue {
  constructor() {
    this.queue = [];
  }

  enqueue(element) {
    this.queue.push(element);
  }

  dequeue() {
    return this.queue.shift();
  }

  front() {
    return this.queue[0];
  }

  isEmpty() {
    return this.queue.length === 0;
  }

  size() {
    return this.queue.length;
  }
}
function solution(priorities, location) {
    const queue = new Queue();

  // 초기 큐에 프로세스와 위치 정보를 저장
  for (let i = 0; i < priorities.length; i++) {
    queue.enqueue({ priority: priorities[i], location: i });
  }

  let order = 0;

  while (!queue.isEmpty()) {
    const currentProcess = queue.dequeue();

    // 현재 프로세스의 우선순위보다 높은 프로세스가 있는지 확인
    const hasHigherPriority = queue.queue.some(
      process => process.priority > currentProcess.priority
    );

    if (hasHigherPriority) {
      queue.enqueue(currentProcess); // 우선순위가 더 높은 프로세스가 있다면 다시 큐에 넣음
    } else {
      order++;

      // 찾고자 하는 프로세스인 경우 순서 반환됨
      if (currentProcess.location === location) {
        return order;
      }
    }
  }
}
```
---
# 목요일 : 스택 문제 풀이 및 발표

## 1. [올바른 괄호(Stack)](https://school.programmers.co.kr/learn/courses/30/lessons/12909)
### 유키의 풀이
```js
function solution(s){
    var answer = 0;
    
    for(const str of s){
        answer+=str==='('?1:-1;
        if(answer<0) return false
    }

    return answer===0?true:false;
}
```
### MZ의 풀이
```js
function solution(s) {
  let count = 0;

  for (let i = 0; i < s.length; i++) {
    if (s[i] === "(") {
      // '('인 경우 카운터 증가
      count++;
    } else if (s[i] === ")") {
      // ')'인 경우
      if (count > 0) {
        // 개수가 0보다 크면 카운터 감소
        count--;
      } else {
        // 개수가 0이면 false 반환 (조기 반환)
        return false;
      }
    }
  }

  // 루프를 마친 후에도 개수가 0이면 true, 그렇지 않으면 false 반환
  return count === 0;
}
```
### BASH의 풀이
```js
function solution(s) {
    answer = true;
    stack = [];
    
    for (let x of s) {
        if (x === '(') {
            stack.push(x);
        } else if (x === ')') {
            // 스택에 아이템이 있으면 팝
            if (stack.length) {
                stack.pop();
            } else {
                return false;
            }
        }
    }
    
    // 문자열을 다 탐색한 후에 stack에 문자가 남아있으면 false
    if (stack.length) {
        answer = false;
    }

    return answer;
```
### 야나의 풀이
```js
class Stack {
    constructor(){
        this.arr = [];
        this.idx = 0;
    }
    push(item){
        this.arr[this.idx++] = item;
    }
    pop(){
        if(this.idx == 0) return null;
        const result = this.arr[--this.idx];
        return result;
    }
    isEmpty(){
        if(this.idx == 0) return true;
        return false;
    }
}
function solution(s){
    const stack = new Stack();
    for(const bracket of s.split('')){
        if(bracket=="("){
            stack.push(bracket);
        }else{
            if(stack.isEmpty()){
                return false;
            }
            stack.pop();
        }
    }
    return stack.isEmpty();
}
```

---
# 금요일 : Heap 자료구조 공부 및 발표(문제 풀어오기)

# Q. Heap자료구조는 완전 정렬 상태일까요, 불완전 정렬 상태일까요?
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
# 배열로 표현되는 Heap(완전 이진트리 형식이기 때문)
![](https://i.imgur.com/3sUWVY2.png)
# Heap Sort
![](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)
## 1. [더 맵게(Heap)](https://school.programmers.co.kr/learn/courses/30/lessons/42626)
### 유키의 풀이
```js
class MinHeap {
  constructor() {
    this.heap = [];
  }

  size() {
    return this.heap.length;
  }
      
    // 값을 넣되, 오름차 순 정렬함
  push(value) {
    this.heap.push(value);
    let currentIndex = this.heap.length - 1;

    while (
      currentIndex > 0 &&
      this.heap[currentIndex] < this.heap[Math.floor((currentIndex - 1) / 2)]
    ) {
      const temp = this.heap[currentIndex];
      this.heap[currentIndex] = this.heap[Math.floor((currentIndex - 1) / 2)];
      this.heap[Math.floor((currentIndex - 1) / 2)] = temp;
      currentIndex = Math.floor((currentIndex - 1) / 2);
    }
  }

    // 값을 빼되, 오름차 순 정렬 함
  pop() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();

    const minValue = this.heap[0];
    this.heap[0] = this.heap.pop();
    let currentIndex = 0;

    while (currentIndex * 2 + 1 < this.heap.length) {
      let minChildIndex = currentIndex * 2 + 2 < this.heap.length && this.heap[currentIndex * 2 + 2] < this.heap[currentIndex * 2 + 1] ? currentIndex * 2 + 2 : currentIndex * 2 + 1;

      if (this.heap[currentIndex] < this.heap[minChildIndex]) {
        break;
      }

      const temp = this.heap[currentIndex];
      this.heap[currentIndex] = this.heap[minChildIndex];
      this.heap[minChildIndex] = temp;
      currentIndex = minChildIndex;
    }

    return minValue;
  }

  peek() {
    return this.heap[0];
  }
}
function solution(scoville, K) {
    var answer = 0;
    
    const minHeap=new MinHeap();
    
    //minHeap 생성
    for(const sco of scoville){
        minHeap.push(sco);
    }
    
    while(minHeap.size()>=2 && minHeap.peek()<K){
        //1,2번째 음식 스코필 구해서 새로운 스코빌 음식 만들기
        const first=minHeap.pop();
        const second=minHeap.pop();
        const mixedFood=first+(second*2);
        
        //새로운 스코필 음식 heap에 넣기
        minHeap.push(mixedFood);
        answer+=1;
    }
    
    return minHeap.peek()>=K ? answer : -1
    
    
}
```
### MZ의 풀이
```
60분 후에 공개됩니다.
```
### BASH의 풀이
```js
class MinHeap {
    constructor() {
        this.heap = [];
    }

    push(value) {
        this.heap.push(value);
        this.heapifyUp();
    }

    pop() {
        if (this.isEmpty()) {
            return null;
        }
        if (this.size() === 1) {
            return this.heap.pop();
        }

        const root = this.heap[0];
        this.heap[0] = this.heap.pop();
        this.heapifyDown();

        return root;
    }

    heapifyUp() {
        let index = this.size() - 1;
        while (index > 0) {
            const parentIndex = Math.floor((index - 1) / 2);
            if (this.heap[index] < this.heap[parentIndex]) {
                this.swap(index, parentIndex);
                index = parentIndex;
            } else {
                break;
            }
        }
    }

    heapifyDown() {
        let index = 0;
        const length = this.size();

        while (true) {
            const leftChildIndex = 2 * index + 1;
            const rightChildIndex = 2 * index + 2;
            let smallestChildIndex = index;

            if (
                leftChildIndex < length &&
                this.heap[leftChildIndex] < this.heap[smallestChildIndex]
            ) {
                smallestChildIndex = leftChildIndex;
            }

            if (
                rightChildIndex < length &&
                this.heap[rightChildIndex] < this.heap[smallestChildIndex]
            ) {
                smallestChildIndex = rightChildIndex;
            }

            if (index !== smallestChildIndex) {
                this.swap(index, smallestChildIndex);
                index = smallestChildIndex;
            } else {
                break;
            }
        }
    }

    swap(i, j) {
        const temp = this.heap[i];
        this.heap[i] = this.heap[j];
        this.heap[j] = temp;
    }

    size() {
        return this.heap.length;
    }

    isEmpty() {
        return this.size() === 0;
    }
}
function solution(scoville, K) {
    const heap = new MinHeap();
    scoville.forEach(value => heap.push(value));

    let mixCount = 0;

    while (heap.size() > 1 && heap.heap[0] < K) {
        const first = heap.pop();
        const second = heap.pop();
        const newScoville = first + 2 * second;
        heap.push(newScoville);
        mixCount++;
    }

    return heap.heap[0] >= K ? mixCount : -1;
}
```
### 야나의 풀이
```js
class Heap{
    constructor(){
        this.items = [];
    }
    //값을 서로 바꾸는 메소드
    swap(index1, index2){
        let temp = this.items[index1]; // items의 index1의 값을 temp(임시공간)에 담음
        this.items[index1] = this.items[index2]; // index1에 index2의 값을 저장
        this.items[index2] = temp; // index2에 index1의 값을 temp에 넣어놓은 값을 저장
    }
    //부모 인덱스 반환
    parentIndex(index){
        return Math.floor((index-1) / 2);
    }
    //왼쪽 자식 인덱스 반환
    leftChildIndex(index){
        return index * 2 + 1;
    }
    //오른쪽 자식 인덱스 반환
    rightChildIndex(index){
        return index * 2 + 2;
    }
    //부모 노드 반환
    parent(index){
        return this.items[this.parentIndex(index)];
    }
    //왼쪽 자식 노드 반환
    leftChild(index){
        return this.items[this.leftChildIndex(index)];
    }
    //오른쪽 자식 노드 반환
    rightChild(index){
        return this.items[this.rightChildIndex(index)];
    }
    //최대-최댓값 / 최소힙-최솟값 반환
    peek(){
        return this.items[0];
    }
    //힙 크기(항목 개수) 반환
    size(){
        return this.items.length;
    }
}
class MinHeap extends Heap{
    bubbleUp(){
        let index = this.items.length-1;
        while(this.parent(index) !==undefined && this.parent(index) > this.items[index]){
            this.swap(index, this.parentIndex(index));
            index = this.parentIndex(index);
        }
    }
    bubbleDown(){
        let index = 0;
        while(this.leftChild(index) !==undefined && (this.leftChild(index) < this.items[index] || this.rightChild(index) < this.items[index])){
            let smallerIndex = this.leftChildIndex(index);
            if(this.rightChild(index) !==undefined && this.rightChild(index) < this.items[smallerIndex]){
                smallerIndex = this.rightChildIndex(index);
            }
            this.swap(index, smallerIndex);
            index = smallerIndex;
        }
    }
    // 힙에 원소 추가
    push(item){
        this.items[this.items.length] = item;
        this.bubbleUp();
    }
    // 최소힙-최솟값 / 최대힙-최댓값 반환
    poll(){
        let item = this.items[0]; // 첫번째 원소 keep
        this.items[0] = this.items[this.items.length - 1]; // 맨 마지막 원소를 첫번째 원소로 복사
        this.items.pop(); // 맨 마지막 원소 삭제
        this.bubbleDown();
        return item; // keep해둔 값 반환
    }
}
class MaxHeap extends MinHeap{
    bubbleUp(){
        let index = this.items.length - 1;
        while(this.parent(index) !== undefined && this.parent(index) < this.items[index]){
            this.swap(index, this.parentIndex(index));
            index = this.parentIndex(index);
        }
    }
    bubbleDown(){
        let index = 0;
        
        while(this.leftChild(index)  !== undefined && (this.leftChild(index) > this.items[index] || this.rightChild(index) > this.items[index])){
            let largerIndex = this.leftChildIndex(index);
            if(this.rightChild(index)  !== undefined && this.rightChild(index) > this.items[largerIndex]){
                largerIndex = this.rightChildIndex(index);
            }
            this.swap(largerIndex, index);
            index = largerIndex;
        }
    }
}
function solution(scoville, K) {
    const minHeap = new MinHeap();
    for(const scovil of scoville){
        minHeap.push(scovil);
    }
    
    let cnt = 0;
    while(minHeap.size() >= 2 && minHeap.peek() < K){
        const firstScv = minHeap.poll();
        const secondScv = minHeap.poll();
        const newScv = firstScv + (secondScv*2);
        minHeap.push(newScv);
        cnt++;
    }
    return minHeap.peek() >= K ? cnt : -1;
}
```


---
# 회고
 - 야나 : 
	 - 어제까지는 JAVA로 풀다가 Js로 문제 풀려니까 너무 기쁘고 좋았는데요, 오늘 Heap을 공부하면서는 JAVA가 그리워졌습니다.. PQ.... Stack과 Queue 그리고 Heap을 이번주 학습한 언어인 Js로 구현해보니 재밌기도 하고, 각 언어의 특성에 대해서도 생각해보게 된 것 같아 좋았습니다.
	   팀원들에게 코드를 설명해보면서, 코드의 가독성과, 읽기 쉬운 코드를 작성하는것에 대해서 다시 생각해보게 된것도 좋았습니다 :)
 - 유키 : 
	 - 이번 스터디 시간을 통해 Heap 알고리즘을 다시 공부해보면서 잘못 알고있던 지식도 바로잡을 수 있었고, 각자 풀어온 문제를 공유해보면서 다양한 접근 방식에 대해 알 수 있어서 유익한 시간이였습니다!
 - MZ : 
	 - VOD로 배운 자바 스크립트 코드를 바탕으로 여러 코딩 테스트를 풀어봤는데,  기존에 강의에서 다뤘던 부분을 더 생각하게 되고, 몰랐던 것들도 많이 배웠습니다. 이해가 잘 안되는 부분은 조원들의 친절한 설명 덕분에 많은 도움이 되었습니다.  물론, GPT형님의 도움도 많이 받아서 OpenAI의 개발팀에게 감사 인사드립니다.
 - 배씨 : 
	 - 팀스터디를 진행하는 동안 여러 자료구조와, 알고리즘에 대해 다시 학습하며 리마인드 할 수 있어서 좋았습니다.  또한 팀원들의 다양한 문제 접근 방식을 보며,  그동안 나는 익숙한 언어로만 풀며 많은 생각과 접근방식에 대해 충분히 생각을 하지 않은점에 반성도 되고 자극도 받아 좋았습니다!