---
layout: single
title:  "Algorithm Programmers 올바른 괄호"
categories: algorithm
tag: [Java, algorithm, stack, programmers, 프로그래머스, 올바른 괄호]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## Programmers 올바른 괄호

  ![올바른 괄호](/assets/img/problem1.png)


```java
import java.util.*;

class Solution {
    boolean solution(String s) {
        boolean answer = true;
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);

            if (c == '(') stack.push(c);

            if (c == ')') {
                if (stack.size() == 0) {
                    return false;
                } else stack.pop();
            }
        }
        return (stack.size() == 0 ? true : false);
    }
}
```
