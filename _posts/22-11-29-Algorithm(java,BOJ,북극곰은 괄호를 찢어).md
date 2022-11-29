---
layout: single
title:  "Algorithm BOJ 북극곰은 괄호를 찢어 25918"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 그리디, 스택 백준25918]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (북극곰은 괄호를 찢어)
[https://www.acmicpc.net/problem/25918](https://www.acmicpc.net/problem/25918)

### 문제
![북극곰은 괄호를 찢어](/assets/img/BOJ25918.jpg)

### 풀이
<li>변수 N, s</li>
<li>깊이체크를 위한 d, dmax 변수</li>
<li>반복문으로 비어있거나 이전에넣은문자가 이번것과 같으면</li>
<li>문자를넣고 깊이를 높이고</li>
<li>아닐경우 문자를 빼고 깊이를 낮추고</li>
<li>dMax는 항상 높았던걸로 갱신</li>

### 슈도코드
<li>var for N, s</li>
<li>var for d, dMax</li>
<li>loop for(0 ~ s.length) </li>
<li>if stack empty or peek = s[i]</li>
<li>push (i) in stack, plus d</li>
<li>else pop from stack, minus d, renew dMax</li>
<li>print -1 if stack empty</li>
<li>print dmax if stack is not empty</li>

### 코드구현
```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<Character> stack = new Stack<>();
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        String s = sc.next();

        int d = 0;
        int dMax = 0;

        for (int i = 0; i < s.length(); i++) {
            if (stack.empty() || stack.peek() == s.charAt(i)) {
                stack.push(s.charAt(i));
                d++;
            } else {
                stack.pop();
                dMax = Math.max(dMax, d);
                d--;
            }
        }

        if (!stack.empty()) {
            System.out.println(-1);
        } else {
            System.out.println(dMax);
        }
    }
}
```
