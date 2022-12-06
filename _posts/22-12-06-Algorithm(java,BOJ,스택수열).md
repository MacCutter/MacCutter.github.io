---
layout: single
title:  "Algorithm BOJ 스택수열 1874"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 스택, 백준1874]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 스택수열
[https://www.acmicpc.net/problem/1874](https://www.acmicpc.net/problem/1874)

### 문제
![스택수열](/assets/img/BOJ1874.jpg)

### 풀이
<li>스택에 숫자를 push하면 + pop하면 - 를 출력하는 문제</li>
<li>수열을 A배열에 입력받기</li>
<li>불리언은 true로 초기화</li>
<li>num변수 1로 초기화(1부터 오름차순으로 넣기위함)</li>
<li>반복문(0~N) 수열(i)번째수를 현재수로 지정</li>
<li>while로 현재수가 num변수 보다 클시 스택에 해당숫자 까지 모두 num++하면서 넣기</li>
<li>while이 끝나면 무조건 pop과 - 를 기록</li>
<li>else는 변수에 pop을 넣고 (i)번째수열보다 크면 NO 출력, false입력, break</li>
<li>(i)번째 수열보다 크진않으면 pop은 이미했으므로 -만 기록</li>
<li>스트링버퍼 출력</li>



### 코드구현
```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int[] A = new int[N];
        for (int i = 0; i < N; i++) {
            A[i] = sc.nextInt();
        }
        StringBuffer bf = new StringBuffer();
        Stack<Integer> stack = new Stack<>();
        boolean result = true;
        int num = 1;
        for (int i = 0; i < N; i++) {
            int su = A[i];
            if(su >= num) {
                while (su >= num) {
                    stack.push(num++);
                    bf.append("+\n");
                }
                stack.pop();
                bf.append("-\n");
            } else {
                int n = stack.pop();
                if (n > su) {
                    System.out.println("NO");
                    result = false;
                    break;
                } else {
                    bf.append("-\n");
                }
            }
        }
        System.out.println(bf.toString());
    }
}
```
