---
layout: single
title:  "Algorithm BOJ ATM(삽입정렬문제) 11399"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 구현, 정렬, 백준11399]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ ATM
[https://www.acmicpc.net/problem/11399](https://www.acmicpc.net/problem/11399)

### 문제
![ATM](/assets/img/BOJ11399.jpg)

### 풀이
<li>수행시간이 짧은순서대로 ATM을인출해야 결국 최소시간이 나온다</li>
<li>배열에삽입하고 정렬후 합배열을 생성하고 그합배열의값을 전부 sum</li>
<li>Sort를 사용하지않고 삽입정렬을 직접 구현해본 문제</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int[] A = new int[N];
        int[] S = new int[N];
        for (int i = 0; i < N; i++) {   // 배열에 나열
            A[i] = sc.nextInt();
        }
        // 삽입정렬
        for (int i = 1; i < N; i++) {
            int key = A[i];
            int j = i - 1;
            while (j >= 0 && A[j] > key) {  // while을돌며 j = -1이되면(앞에까지 다 검색했다 의미)
                A[j + 1] = A[j];            // 키값자리를 기존가장큰수로 덮음
                j--;                        // 바꾼수를이전 앞자리들과도 비교하려고 j--
            }
            A[j + 1] = key;
        }
        // 합배열 생성
        S[0] = A[0];
        for (int i = 1; i < N; i++) {
            S[i] = S[i - 1] + A[i];
        }
        // 합배열값 sum
        int sum = 0;
        for (int i = 0; i < N; i++) {
            sum += S[i];
        }
        System.out.println(sum);
    }
```
