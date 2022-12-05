---
layout: single
title:  "Algorithm BOJ 최소값 찾기 11003"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 우선순위큐, 덱, 슬라이딩 윈도우, 백준11003]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 최소값 찾기
[https://www.acmicpc.net/problem/11003](https://www.acmicpc.net/problem/11003)

### 문제
![최소값 찾기](/assets/img/BOJ11003.jpg)

### 풀이
<li>슬라이딩윈도우, 데크를 사용하는 문제, 일반적인 정렬nlogn을 사용하면 시간초과</li>
<li>최소값의 범위가 i - L + 1 이므로 L 과 마찬가지로 생각</li>
<li>입력값 N, L 받기</li>
<li>반복문(0 ~ N)에서</li>
<li>now변수에 nextToken 하나 입력</li>
<li>기존데크가 비어있지 않으면서 and now보다 큰수면 removeLast</li>
<li>Node(now,i)로 입력받은값 추가</li>
<li>L범위 보다 벗어난 인덱스는 removeFirst</li>
<li>bw.write로 첫번째값(이미정렬상태이므로 제일 작은수) 출력</li>

### 코드구현
```java
import java.io.*;
import java.util.Deque;
import java.util.LinkedList;
import java.util.Scanner;
import java.util.StringTokenizer;

public class Main {
    public static final Scanner sc = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int L = Integer.parseInt(st.nextToken());
        st = new StringTokenizer(br.readLine());
        Deque<Node> deque = new LinkedList<>();
        for (int i = 0; i < N; i++) {
            int now = Integer.parseInt(st.nextToken());

            // 데크가 비어있지 않으면서 and 기존의 수들 중 새로운값(now)보다 크면 제거
            while (!deque.isEmpty() && deque.getLast().value > now) {
                deque.removeLast();
            }
            deque.addLast(new Node(now, i));
            //범위에서 벗어난 값 덱에서 제거 (i - L + 1)
            if (deque.getFirst().index <= i - L) {
                deque.removeFirst();
            }
            bw.write(deque.getFirst().value + " ");
        }
        bw.flush();
        br.close();
    }

    static class Node {
        public int value;
        public int index;

        Node (int value, int index) {
            this.value = value;
            this.index = index;
        }
    }
}
```
