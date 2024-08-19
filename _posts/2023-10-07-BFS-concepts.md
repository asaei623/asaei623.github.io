---
title: "BFS 개념 정리"
excerpt: "BFS 기본 풀이 방법과 4가지 응용 유형"

categories:
    - Algorithm
tags: # 포스트 태그
    - [algorithm, python, BFS]

permalink: /categories1/BFS-concepts/

toc: true
toc_sticky: true

date: 2023-10-07
last_modified_at: 2023-10-07
---

## 🍊BFS 알고리즘

**Breadth Firth Search**는 다차원 배열에서 각 칸을 방문할 때 너비를 우선으로 방문하는 알고리즘이다.

그래프라는 자료구조에서 모든 노드를 방문하기 위한 알고리즘이다.

### 알고리즘 방법

> 1. `시작칸`을 `큐`에 넣어 `방문 표시`를 남긴다.
> 2. `큐`에서 원소를 꺼내 상하좌우 인접한 칸에 대해 3번을 진행한다.
> 3. 이미 방문한 칸이면 아무것도 하지 않고, **처음 방문한 칸**이면 `방문 표시를` 남기고 `큐`에 넣는다.
> 4. `큐`가 **빌 때까지** 2번을 반복한다.

BFS는 정석적인 코드가 있기 때문에 그 틀을 외워두는 것이 좋다.

### 시간 복잡도

모든 칸이 큐에 1번씩 들어가기 때문에 N개의 칸에 대해 시간 복잡도는 **O(N)**이다.

### 자주 하는 실수

1. 시작점에 `방문 표시`를 남기지 않는다.
2. `큐`에 **넣을 때**가 아닌 빼낼 때 `방문 표시`를 남겨서 시간 초과 혹은 메모리 초과가 발생한다.

<br>

## 🍊 예시

📝 **문제** [BOJ 1926 그림](https://www.acmicpc.net/problem/1926)
📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/BFS/%EA%B7%B8%EB%A6%BC.py)**

### 문제에서 요구하는 것

Flood Fill을 수행하는 문제다.

1. 상하좌우로 연결된 그림의 크기를 알아내기
2. 도화지에 있는 모든 그림을 찾아내기
    - BFS의 시작점을 알아내면 된다.

### 시간 복잡도

칸이 큐에 한 번씩만 들어가기 때문에 칸의 개수를 NM이라 할 때 시간 복잡도는 O(NM)이다.

<br>

## 🍊 응용 1 - 거리 측정

📝 **문제** [BOJ 2178 미로탐색](https://www.acmicpc.net/problem/2178) 📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/BFS/%EB%AF%B8%EB%A1%9C_%ED%83%90%EC%83%89.py)**

### 풀이 방법

-   하위 level 노드로 이동할 때 **거리가 1 증가**하는 것과 같다.
-   BFS를 동일하게 수행하면서 거리를 저장하면 된다.

<br>

## 🍊 응용 2 - 시작점이 여러 개일 때

📝 **문제** [BOJ 7576 토마토](https://www.acmicpc.net/problem/7576) 📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/BFS/%ED%86%A0%EB%A7%88%ED%86%A0.py)**

### 풀이 방법

-   **모든 시작점**을 **큐**에 넣고 BFS를 시작하면 자연스럽게 여러 시작점에 대해 동시에 BFS가 돌아가는 것과 같이 된다.

<br>

## 🍊 응용 3 - 시작점이 두 종류일 때

📝 **문제** [BOJ 4179 불!](https://www.acmicpc.net/problem/4179) 📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/BFS/%EB%B6%88!.py)**

### 풀이 방법

-   종류가 다른 시작점들에 대해서 **각각 BFS를 실행**한다. 이 문제는 불의 전파만 지훈이에게 영향을 주고 불의 전파는 지훈이에게 영향을 받지 않는다. 따라서 불의 전파를 끝낸 다음, 지훈의 BFS를 실행하는 것으로 문제를 해결할 수 있었다.

-   만약 A, B의 전파가 서로에게 영향을 준다면, 두 BFS를 동시에 진행시켜야 하기 때문에 지금의 방법으로는 해결할 수 없다.

<br>

## 🍊 응용 4 - 1차원에서의 BFS

📝 **문제** [BOJ 1697 숨바꼭질](https://www.acmicpc.net/problem/1697) 📝 **[내 풀이](https://github.com/asaei623/Algorithm-Study-Python/blob/main/BFS/%EC%88%A8%EB%B0%94%EA%BC%AD%EC%A7%88.py)**

### 풀이 방법

-   2차원에서 상하좌우 이동 시 거리를 +1 했던 것처럼, 수빈이가 수직선에서 **-1, +1, \*2로 이동 시 거리를 +1 하는 것**으로 생각한다.
-   주의 할 것은, 문제에서 수빈이의 **이동 범위가 제한되어 있지 않다**는 것이다. 이 문제에서는 수빈이가 `0 <= N <= 100,000`을 벗어나는 것이 비효율적이기 때문에(갈 이유가 없기 때문에) 이대로 이동 범위를 제한해도 문제가 없지만, _다른 문제에서는 그렇지 않을 수도 있기_ 때문에 주의해서 살펴야 한다.

<br>

---

<span style="color:#888888">출처</span>
[https://blog.encrypted.gg/941](https://blog.encrypted.gg/941)
