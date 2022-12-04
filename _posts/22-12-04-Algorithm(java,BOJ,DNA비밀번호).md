---
layout: single
title:  "Algorithm BOJ DNA비밀번호 12891"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 문자열, 슬라이딩 윈도우, 백준12891]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ DNA비밀번호
[https://www.acmicpc.net/problem/12891](https://www.acmicpc.net/problem/12891)

### 문제
![DNA비밀번호](/assets/img/BOJ12891.jpg)

### 풀이
<li>S배열과 비밀번호체크배열(4자리) 저장</li>
<li>P크기의 배열을 만들어 현재상태 배열에 각 알파벳 갯수대로 카운트</li>
<li>현재상태 배열과 비밀번호 체크배열을 비교하여 맞는갯수 카운트</li>
<li>P크기를 유지하며 앞에하나ADD 뒤에하나 REMOVE 하며 맞는갯수 카운트</li>
<li>카운트 출력</li>

### 코드구현
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    static int checkArr[];
    static int myArr[];
    static int checkSecret;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int S = Integer.parseInt(st.nextToken());
        int P = Integer.parseInt(st.nextToken());
        int result = 0;
        char A[] = new char[S];
        checkArr = new int[4];  // ACGT 4글자 체크하기
        myArr = new int[4];
        checkSecret = 0;        // check와 my를 비교해서 4개가 모두일치하면 result 추가

        A = br.readLine().toCharArray();
        st = new StringTokenizer(br.readLine());
        for (int i = 0; i < 4; i++) {
            checkArr[i] = Integer.parseInt(st.nextToken());

            if (checkArr[i] == 0) checkSecret++;    // 어떤자리가 필요한게 0개면 해당 자리는 무조건 일치하므로 checkSecret++

        }

        for (int i = 0; i < P; i++) {   // 초기P만큼 배치후
            Add(A[i]);
        }
        if (checkSecret == 4) result++; // 4 자리모두 일치하면 result ++

        for (int i = P; i < S; i++) {   // 하나씩 뒤에add 앞에 remove 하며 result++
            int j = i - P;
            Add(A[i]);
            Remove(A[j]);
            if (checkSecret == 4) result++;
        }
        System.out.println(result);
        br.close();
    }

    private static void Add(char c) {
        switch (c) {
            case 'A':
                myArr[0]++;
                if (myArr[0] == checkArr[0])
                    checkSecret++;
                break;
            case 'C':
                myArr[1]++;
                if (myArr[1] == checkArr[1])
                    checkSecret++;
                break;
            case 'G':
                myArr[2]++;
                if (myArr[2] == checkArr[2])
                    checkSecret++;
                break;
            case 'T':
                myArr[3]++;
                if (myArr[3] == checkArr[3])
                    checkSecret++;
                break;
        }
    }

    private static void Remove(char c) {
        switch (c) {
            case 'A':
                if (myArr[0] == checkArr[0])
                    checkSecret--;
                myArr[0]--;
                break;
            case 'C':
                if (myArr[1] == checkArr[1])
                    checkSecret--;
                myArr[1]--;
                break;
            case 'G':
                if (myArr[2] == checkArr[2])
                    checkSecret--;
                myArr[2]--;
                break;
            case'T':
                if (myArr[3] == checkArr[3])
                    checkSecret--;
                myArr[3]--;
                break;
        }
    }
}
```
