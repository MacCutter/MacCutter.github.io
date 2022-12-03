---
layout: single
title:  "Algorithm BOJ 좋다(좋은수구하기) 1253"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 정렬, 이분탐색, 투포인터, 백준1253]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 좋다(좋은수구하기)
[https://www.acmicpc.net/problem/1253](https://www.acmicpc.net/problem/1253)

### 문제
![좋다(좋은수구하기)](/assets/img/BOJ1253.jpg)

### 풀이
<li>입력받은 N을 배열A로 오름차순 정렬</li>
<li>투포인터 i = 0 , j = N - 1 로 시작</li>
<li>start와 end 를 합친것이 좋은수(find) 라고 했을때 반복문으로</li>
<li>A = find 일경우 카운트++</li>
<li>중첩 조건문으로 좋은수가 자기자신이면 제외(두 수의 합인 조건이므로)</li>
<li>A[i]+A[j] < find 일경우 start++ (작은숫자를 늘려주기)</li>
<li>A[i]+A[j] > find 일경우 end -- (큰숫자를 줄여주기)</li>
<li>출력 카운트</li>

### 코드구현
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int count = 0;
        long[] A = new long[N];
        StringTokenizer st = new StringTokenizer(br.readLine());

        for (int i = 0; i < N; i++) {
            A[i] = Long.parseLong(st.nextToken());
        }

        Arrays.sort(A);
        for (int k = 0; k < N; k++) {
            long find = A[k];
            int i = 0;          //투포인터 i 와 j
            int j = N - 1;

            while (i < j) {
                if (A[i] + A[j] == find) {
                    if (i != k && j != k) {     // 두수의 합이어야 하므로 좋은수가 자기자신이면 제외
                        count++;
                        break;
                    } else if (i == k) {
                        i++;
                    } else if (j == k) {
                        j--;
                    }
                } else if (A[i] + A[j] < find) {
                    i++;
                } else {
                    j--;
                }
            }
        }
        System.out.println(count);
        br.close();
    }
}
```
