---
layout: single
title:  "Algorithm BOJ 연속된 자연수의 합 2018"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 그리디, 스택, 백준2018]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (연속된 자연수의 합)
[https://www.acmicpc.net/problem/2018](https://www.acmicpc.net/problem/2018)

### 문제
![연속된 자연수의 합](/assets/img/BOJ2018.jpg)

### 풀이
<li>N의자연수를 받으면 연속된 자연수의 합이 N이 되는 경우의 수 더하는 문제</li>
<li>투포인터 startIdx, endIdx를 이용해 숫자를 증가시켜가며 진행</li>
<li>cnt = 1인 이유는 N이 마지막 자기자신(N) 만으로 구성된것을 미리 카운팅</li>
<li>startIdx, endIdx 1인 이유는 숫자1부터 더해지는 의미가 있어서</li>
<li>sum도 위와 마찬가지로 1부터 더해진 의미가 있어서</li>
<li>반복문(while (!endIdx == N)) 돌면서 sum == N 인경우 카운팅</li>
<li>sum = N 경우 endIdx하나 늘려주고 카운팅++</li>
<li>sum > N 경우 sum-startIdx(이전시작을 없애고) startIdx++(다음시작으로 당겨주고)</li>
<li>sum < N 경우 endIdx++(끝에하나 늘려주고) sum+endIdx(그값을 더해주고)</li>
<li>출력</li>

### 슈도코드
<li>var for N</li>
<li>var for cnt, startIdx, endIdx</li>
<li>loop while(!endIdx == N) </li>
<li>if (sum == N) endIdx++, cnt++</li>
<li>if (sum > N) sum = sum - startIdx, startIdx++</li>
<li>if (sum < N) endIdx++, sum = sum+endIdx</li>
<li>print cnt</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int cnt = 1;
        int startIdx = 1;
        int endIdx = 1;
        int sum = 1;

        while (endIdx != N) {
            if (sum == N) {
                cnt++;
                endIdx++;
                sum = sum + endIdx;
            } else if (sum > N) {
                sum = sum - startIdx;
                startIdx++;
            } else {
                endIdx++;
                sum = sum + endIdx;
            }
        }
        System.out.println(cnt);
    }
}    
```
