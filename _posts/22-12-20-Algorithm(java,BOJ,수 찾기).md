---
layout: single
title:  "Algorithm BOJ 수 찾기 1920"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 그래프, 탐색, DFS/BFS, 백준1920]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 수 찾기
[https://www.acmicpc.net/problem/1920](https://www.acmicpc.net/problem/1920)

### 문제
![수 찾기](/assets/img/BOJ1920.jpg)

### 풀이
<li>이진탐색을 하는 문제</li>
<li>정렬된(기본적으로 오름차순이지만 내림차순은 순서를 반대로 하면 된다) 배열에서 중간값을 찾고 비교하며 데이터를 절반씩 줄여나가며 탐색</li>
<li>logN의 속도를 보여준다(16개의 데이터로 가정하면 최대 4번의연산)</li>
<li>반복,조건문이 섞여있어서 구현하는 방법을 반복적으로 연습해봐야 할것같다</li>

### 코드구현
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int[] A = new int[N];
        for (int i = 0; i < N; i++) {
            A[i] = sc.nextInt();
        }
        Arrays.sort(A);
        int M = sc.nextInt();
        for (int i = 0; i < M; i++) {
            boolean find = false;
            int target = sc.nextInt();
            int start = 0;
            int end = N - 1;
            while (start <= end) {
                int midi = (start + end) / 2;
                int midv = A[midi];
                if (midv > target) {
                    end = midi - 1;
                } else if (midv < target) {
                    start = midi + 1;
                } else {
                    find = true;
                    break;
                }
            }
            if (find) {
                System.out.println(1);
            } else {
                System.out.println(0);
            }
        }
    }
}

```
