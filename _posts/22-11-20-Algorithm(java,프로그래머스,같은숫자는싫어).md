---
layout: single
title:  "Algorithm Programmers 같은 숫자는 싫어"
categories: algorithm
tag: [Java, algorithm, stack, programmers, 프로그래머스, 같은 숫자는 싫어]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 프로그래머스 알고리즘 문제(같은 숫자는 싫어)

  ![같은 숫자는 싫어](/assets/img/problem.png)


```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {

        ArrayList<Integer> answer = new ArrayList<>();

        answer.add(arr[0]);

        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] != arr[i]) {
                answer.add(arr[i]);
            }
        }
        return answer.stream().mapToInt(i -> i).toArray();
    }
}
```
