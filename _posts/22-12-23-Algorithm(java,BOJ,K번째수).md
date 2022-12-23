---
layout: single
title:  "Algorithm BOJ K번째수 1300"
categories: algorithm
tag: [Java, algorithm, BOJ, 자료구조, 정렬, 이진탐색, 백준1300]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## K번째수
[https://www.acmicpc.net/problem/1300](https://www.acmicpc.net/problem/1300)

### 문제
![K번째수](/assets/img/BOJ1300.jpg)

### 풀이
<li>블루레이 크기가 모두같고 녹화 순서가 바뀌지 않아야함의 조건으로 이진탐색을 추측</li>
<li>레슨 최대값을 시작인덱스, 레슨누적합을 끝인덱스로 시작</li>
<li>조건문에서 모두 저장할수 있다면 블루레이 크기를 줄이고 저장할수없다면 블루레이 크기를 늘리는 방식으로 최소값 도출</li>

### 코드구현
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();   // 9
        int M = sc.nextInt();   // 3
        int A[] = new int[N];
        int start = 0;
        int end = 0;
        for (int i = 0; i < N; i++) {
            A[i] = sc.nextInt();    // 1 2 3 4 5 6 7 8 9
            if (start < A[i]) start = A[i]; // 레슨 최대값을 시작인덱스로 저장(0부터해서 높은값이 게속 갱신)
            end = end + A[i];   // 모든레슨 총합 저장(누적합)
        }
        while (start <= end) {
            int middle = (start + end) / 2;
            int sum = 0;
            int count = 0;
            for (int i = 0; i < N; i++) {
                if (sum + A[i] > middle) {  // i = 0,1,2,~ 6일때 첫번째 진입
                    count++;                // 카운트 갯수를 남겨 블루레이 필요갯수가 산출됨
                    sum = 0;                // 블루레이 하나는 끝났으니 그다음레슨 들어갈 블루레이를 위해 초기화
                }
                sum = sum + A[i];
            }
            if (sum != 0) count++;  // 마지막 레슨담은 블루레이가 0이아니면 필요한 갯수이므로 ++
            if (count > M) {  // 첫케이스는 false(middle 값으로 count만큼 저장 가능)
                start = middle + 1;
            } else
                end = middle - 1; // 첫케이스에서 충분히 저장이되니 미드값을 내려봄
        }
        System.out.println(start);
    }
}
```
