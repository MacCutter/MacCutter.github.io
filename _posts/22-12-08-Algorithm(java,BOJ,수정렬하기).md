---
layout: single
title:  "Algorithm BOJ 수정렬하기 2750"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 구현, 정렬, 백준2750]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 수정렬하기
[https://www.acmicpc.net/problem/2750](https://www.acmicpc.net/problem/2750)

### 문제
![수정렬하기](/assets/img/BOJ2750.jpg)

### 풀이
<li>N의 수가적어서 N의2제곱인 버블정렬(크기비교후 앞뒤를 바꾸는)구현</li>
<li>맨앞부터 앞뒤를 비교하며 오름차순이 아닐경우 교체</li>
<li>맨앞은 정렬됐으므로 그다음 반복문에서 N - i 로 배제후 반복</li>
<li>정렬된 배열 출력</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int[] A = new int[N];
        for (int i = 0; i < N; i++) {
            A[i] = sc.nextInt();
        }
        for (int i = 0; i < N - 1; i++) {
            for (int j = 1; j < N - i; j++) {
                if (A[j - 1] > A[j]) {
                    int temp = A[j - 1];
                    A[j - 1] = A[j];
                    A[j] = temp;
                }
            }
        }
        for (int i = 0; i < N; i++) {
            System.out.println(A[i]);
        }
    }
}
```
