---
title: "다이나믹 프로그래밍 개념 정리"
excerpt: ""

categories:
    - Algorithm
tags: # 포스트 태그
    - [algorithm, python, dp]

permalink: /categories/algorithm/2023-08-09-dp-concepts/

toc: true
toc_sticky: true

date: 2023-08-09
last_modified_at: 2023-08-09
---

## 🍊다이나믹 프로그래밍 알고리즘

> **다이나믹 프로그래밍(Dynamic Programming, DP)**은
> 여러 개의 하위 문제를 먼저 푼 후, 그 결과를 쌓아올려 주어진 문제를 해결하는 알고리즘

즉,

1. 문제를 해결하기 위한 `점화식`을 찾아낸다.
2. `점화식`을 이용해 답을 알아낸다.
3. 재귀와 달리 반복문을 통해 배열에 **중간 결과값을 저장**해서 `시간 복잡도`를 극적으로 줄인다.

### 알고리즘 풀이과정

1. 테이블 정의하기
2. 점화식 찾기
3. 초기값 정하기

<br/>

## 🍊 연습 문제 1 : 1로 만들기

📝 **문제** [BOJ 1463 1로 만들기](https://www.acmicpc.net/problem/1463)
📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/DP/1%EB%A1%9C_%EB%A7%8C%EB%93%A4%EA%B8%B0.py)**

### BFS 풀이법

1. 3가지 경로가 있고(*3, *2, +1)
2. 1에서 N이 될 때까지의 최소 거리
   를 구하면 된다.

### DP 풀이법

1. 테이블 정의하기
   D[i] : i를 1로 만들기 위해 필요한 연산 사용 횟수의 최솟값

2. 점화식 찾기

-   구체적인 예시 'D[12] 찾기'
    D[1]부터 D[11]까지 알고 있을 때, D[12]를 어떻게 구할 것인가?
    3가지 경우가 있다.
    1. 12 / 3 = 4 이므로, D[12] = D[4] + 1
    2. 12 / 2 = 6 이므로, D[12] = D[6] + 1
    3. 12 - 1 = 11 이므로, D[12] = D[11] + 1
       따라서 D[12] = min(D[4], D[6], D[11]) + 1
-   D[k]에 대한 식 정리하기
    D[k] = min(D[k/3], D[k/2], D[k-1]) + 1

3. 초기값 정의하기

-   점화식이 굴러갈 수 있게 하는 초기값이 어디까지인지 잘 찾아내야 한다.
-   이 문제의 경우 초기값은,
    D[1] = 0

<br/>

## 🍊 연습 문제 2 : 1, 2, 3 더하기

📝 **문제** [BOJ 9095 1, 2, 3 더하기](https://www.acmicpc.net/problem/9095)
📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/DP/1%2C2%2C3_%EB%8D%94%ED%95%98%EA%B8%B0)**

### 풀이법

1. 테이블 정의하기
   D[i] : i를 1, 2, 3의 합으로 나타내는 방법의 수

2. 점화식 정의하기

-   구체적인 예시 'D[4] 찾기'

    1. D[3]의 방법들에 1만 더하기
    2. D[2]의 방법들에 2만 더하기
    3. D[1]의 방법에 3만 더하기
       따라서 D[4] = D[3] + D[2] + D[1]

-   D[k]에 대해서 정리하기
    D[k] = D[k-1] + D[k-2] + D[k-3]

-   초기값 정의하기
    D[1] = 1
    D[2] = 2
    D[3] = 4

<br/>

---

<span style="color:#888888">출처</span>
[https://blog.encrypted.gg/974](https://blog.encrypted.gg/974)
