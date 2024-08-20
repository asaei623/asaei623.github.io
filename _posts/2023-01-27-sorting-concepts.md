---
title: "정렬(sorting) 개념 정리"
excerpt: "버블 정렬, 합병 정렬, 파이썬 내장 정렬함수"

categories:
    - Algorithm
tags: # 포스트 태그
    - [algorithm, python, sorting]

permalink: /categories/algorithm/2023-01-27-sorting-concepts/

toc: true
toc_sticky: true

date: 2023-01-27
last_modified_at: 2023-01-27
---

> -   버블 정렬, 합병 정렬, 파이썬 내장 정렬함수에 대해 정리했다

-   파이썬을 사용한다.

## 🐥정렬 알고리즘

정렬 알고리즘은 두 가지 시간 복잡도로 분류할 수 있다.

| $O(n^2)$       | $O(nlogn)$ |
| -------------- | ---------- |
| Insertion sort | Quick sort |
| Selection sort | Merge sort |
| Bubble sort    | Heap sort  |

### 시간 복잡도

시간 복잡도란 문제를 푸는데 걸리는 시간을 입력 n의 함수 관계를 사용하여 나타낸 것이다.

알고리즘의 시간복잡도는 주로 **Big-O 표기법**을 사용하는데, 이는 계수를 모두 없앤 뒤 최대 차항만을 표기하는 방법이다.

예를 들어, 어떤 문제를 푸는데 최대 $8n^2 + 2n + 1$번의 연산이 필요하다면 계수를 모두 없앤 식은 $n^2 + n$이 된다.

이 상태에서 최대 차항은 $n^2$이므로, 결과적으로 시간 복잡도는 $O(n^2)$로 표기된다.

## 💧버블 정렬

버블 정렬은 가장 간단한 정렬 방법이다.

> 1. 인접한 두 원소를 비교한다.
> 2. [왼쪽 원소] > [오른쪽 원소] 라면 swap! 한다.
> 3. 가장 큰 원소부터 오른쪽에 정렬된다.
> 4. 데이터가 하나씩 정렬되면서 비교에서 제외된다.

### 📝 문제

[백준 2750 : 수 정렬하기 - Bronze 1](https://velog.io/@asaei623/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%B0%B1%EC%A4%80-2750-%EC%88%98-%EC%A0%95%EB%A0%AC%ED%95%98%EA%B8%B0)

## 🤝합병 정렬

합병 정렬은 분할 정복(Divide and Conquer) 방식으로 설계된 알고리즘이다.

분할 정복 알고리즘은 주로 재귀 함수로 구현되며 다음의 3단계로 이루어진다.

> 1. Divide : 문제 분할
> 2. Conquer : 쪼개진 작은 문제 해결
> 3. Combine : 해결된 작은 문제들을 다시 합침

### 📝 문제

[백준 2751 : 수 정렬하기 2 - Silver 5](https://velog.io/@asaei623/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%B0%B1%EC%A4%80-2751-%EC%88%98-%EC%A0%95%EB%A0%AC%ED%95%98%EA%B8%B0-2)

## 🥧파이썬 정렬함수

하지만 정렬할 일은 많고, 매번 정렬함수를 구현하기는 어렵다.
파이썬에 내장된 정렬함수를 사용하면 편리하게 구현할 수 있다.

[파이썬 정렬 문서 바로가기](https://docs.python.org/ko/3/howto/sorting.html)

### list.sort()

-   리스트의 **메소드**로, 리스트의 **원본**을 정렬된 형태로 바꾸어 놓으며 None을 반환한다.
-   디폴트 값은 오름차순 정렬이지만, key 값에 함수(람다함수)를 보내면 원하는 조건대로 정렬이 가능하다.
    ex) 내림차순 정렬 : reverse에 true를 보내줌

### sorted()

-   정렬된 리스트를 **반환**하는 함수입니다. 인자로 iterable 객체를 받는다.
-   역시 key 값을 통해 원하는 조건으로 정렬이 가능하다.
-   예시 코드
    ```python
    sorted(student_objects, key=attrgetter('age'), reverse=True)
    [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
    ```

### 📝 문제

[백준 10825 : 국영수 - Silver 4](https://velog.io/@asaei623/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%B0%B1%EC%A4%80-10825-%EA%B5%AD%EC%98%81%EC%88%98)

## 📚 과제

[백준 10804 : 카드 역배치 - Bronze 2](https://velog.io/@asaei623/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%B0%B1%EC%A4%80-10804-%EC%B9%B4%EB%93%9C-%EC%97%AD%EB%B0%B0%EC%B9%98)
[백준 12840 : 창용이의 시계 - Bronze 3](https://velog.io/@asaei623/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%B0%B1%EC%A4%80-12840-%EC%B0%BD%EC%9A%A9%EC%9D%B4%EC%9D%98-%EC%8B%9C%EA%B3%84)
백준 11651 : 좌표 정렬하기2 - Silver 2
백준 1758 : 알바생 강호 - Silver 4
백준 1431 : 시리얼 번호 - Silver 3
백준 1946 : 신입 사원 - Silver 1
백준 1026 : 보물 - Silver 4

---

<span style="color:#888888">출처</span>
https://github.com/Altu-Bitu-2/Notice/blob/main/00.%20%EA%B0%95%EC%9D%98%EC%9E%90%EB%A3%8C/01.%20%EC%A0%95%EB%A0%AC.pdf
