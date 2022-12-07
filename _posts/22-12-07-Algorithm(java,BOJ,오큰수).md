---
layout: single
title:  "Algorithm BOJ 오큰수 17298"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 스택, 백준17298]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 오큰수
[https://www.acmicpc.net/problem/17298](https://www.acmicpc.net/problem/17298)

### 문제
![오큰수](/assets/img/BOJ17298.jpg)

### 풀이
<li>스택에 새로 들어오는수가 top보다 크면 오큰수임</li>
<li>마지막은 그다음의 비교대상이 없으니 무조건 -1</li>
<li>스택에 넣는것은 값이아닌 인덱스</li>
<li>첫 비교대상이 없으니 스택에 0번째인덱스는 넣어주고 시작</li>
<li>반복문으로 N+1번째와 N번째 인덱스의 값을 비교하여 더크면 오큰수</li>
<li>오큰수가 없이 스택에 남아있는 인덱스 들에 모두 -1 저장</li>
<li>자연스럽게남는 마지막인덱스와 오큰수가 없던인덱스들이 -1이 됨</li>

### 코드구현
```java
import java.io.*;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        long[] A = new long[N];
        long[] answer = new long[N];

        StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < N; i++) {
            A[i] = Integer.parseInt(st.nextToken());
        }
        Stack<Integer> stack = new Stack<>();
        stack.push(0);
        for (int i = 1; i < N; i++) {
            while (!stack.isEmpty() && A[stack.peek()] < A[i]) {
                answer[stack.pop()] = A[i];
            }
            stack.push(i);
        }
        while (!stack.empty()) {
            answer[stack.pop()] = -1;
        }
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for (int i = 0; i < N; i++) {
            bw.write(answer[i] + " ");
        }
        bw.write("\n");
        bw.flush();
        br.close();
    }
}
```
