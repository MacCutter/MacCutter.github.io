---
layout: single
title:  "Algorithm Programmers 전화번호 목록"
categories: algorithm
tag: [Java, algorithm, Programmers, 해쉬, 프로그래머스 전화번호 목록]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 전화번호 목록
[https://school.programmers.co.kr/learn/courses/30/lessons/42577](https://school.programmers.co.kr/learn/courses/30/lessons/42577)

### 문제
![전화번호 목록](/assets/img/Programmers42577.jpg)

### 풀이
<li>한번호의 모든요소가 다른번호에 하나라도 포함된경우가 있는지 묻는문제(설명에서의 접두어)</li>
<li>해쉬맵 생성하여 Key에 번호,Value에 1을 넣어준다(1은 존재만한다 의미X)</li>
<li>모든 전화번호의 접두어가 해쉬맵전체에 있는지 반복문으로 검색</li>
<li>2중반복문 + 1개의 조건문으로 검색한다</li>
<li>하나라도 검색됐으면 false를 리턴</li>
<li>위의 반복문을 다돌았는데 false가 없었으면 true 리턴</li>

### 코드구현
```java
import java.util.HashMap;

public class 전화번호목록 {
    public boolean solution(String[] phone_book) {
        // HashMap 생성
        HashMap<String,Integer> map = new HashMap<>();
        for (int i = 0; i < phone_book.length; i++) {   // 모든번호를 넣어야해서 0 ~ length 만큼
            map.put(phone_book[i], 1);                  // 1은 크게 의미없음 존재한다.
        }
        // 모든 전화번호의 접두어가 HashMap에 있는지 확인
        for (int i = 0; i < phone_book.length; i++) {   // 폰북에서 0번째 요소를 고르기
            for (int j = 1; j < phone_book[i].length(); j++) {
                if (map.containsKey(phone_book[i].substring(0, j)))
                    return false;
            }
        }
        // 하나도 못찾은경우
        return true;
    }

    public static void main(String[] args) {
        System.out.println(new 전화번호목록().solution(new String[]{"12","123","1235","567","88"}));  // false
        System.out.println(new 전화번호목록().solution(new String[]{"123","456","789"}));             // true

    }
}
```
