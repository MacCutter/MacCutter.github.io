---
layout: single
title:  "Algorithm Programmers 주식가격"
categories: algorithm
tag: [Java, algorithm, Programmers, Stack, 프로그래머스, 주식가격]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 전화번호 목록
[https://school.programmers.co.kr/learn/courses/30/lessons/42584](https://school.programmers.co.kr/learn/courses/30/lessons/42584)

### 문제
![전화번호 목록](/assets/img/Programmers42584.jpg)

### 풀이
<li>첫번째 2중포문 풀이의 경우 늘어나는 j가 i보다 크면 게속 answer인덱스를 ++하며 진행되고 i가 큰경우가 나타나면 break된다</li>
<li>로직은 비슷하게 생각했으나 j에 i + 1이 들어가서 배열앞의 하나씩 배제되는것을 구현하는건 어려웠던것 같다</li>
<li>2중포문 이라서 스택보다 당연히 시간복잡도 높을줄 알았는데 훨씬 높다..</li>
<li>확실하게 코드를보고 시간복잡도를 알기 힘들어서 시간복잡도에 대한공부가 더 필요할것 같다.</li>

### 코드구현
```java
class Solution {
    public int[] solution(int[] prices) {
        int len = prices.length;
        int[] answer = new int[len];
        int i, j;
        for (i = 0; i < len; i++) {
            for (j = i + 1; j < len; j++) {
                answer[i]++;
                if (prices[i] > prices[j])
                    break;
            }
        }
        return answer;
    }
}
```

### 풀이
<li>스택 풀이의 경우 기존에 풀어본 큐문제와 비슷했다</li>
<li>스택에 값을넣지않고 인덱스를 넣어서 진행시키는게 인상적이였다</li>
<li>값이들어갔다 인덱스가 들어갔다해서 구하는게 헷갈린다</li>
<li>스택/큐 유형중에 비슷하게 풀린문제가 벌써 여러번 나온걸로 보아 자주나오는 유형이라 확실히 익혀둬야할것 같음</li>
<li>첫번째 while에서 인덱스를 집어넣고 마지막while에서 인덱스를 빼면서 값을입력해주는걸 기억해야겠다.</li>

```java
public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < prices.length; i++) {
            while (!stack.isEmpty() && prices[stack.peek()] > prices[i]) {
                answer[stack.peek()] = i - stack.peek();    // i - stack.peek()은 후-전 해서 1초 차이라는뜻
                stack.pop();    // 떨어진answer의 인덱스에 표시했기때문에 pop
            }
            stack.push(i); // 가격이 오르기만하면 게속 push
        }// 여기까지 진행하면 진행중 가격이 떨어졌던 인덱스에만 값이 들어가있음 나머지는 밑에 while

        while (!stack.isEmpty()) {
            answer[stack.peek()] = prices.length - stack.peek() - 1;    // 인덱스전체 - 넣을인덱스 - 1 (0부터시작이라)
            stack.pop();
        }

        return answer;
    }
```
