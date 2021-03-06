# 부품 찾기

## 문제

동빈이네 전자 매장에는 부품이 N개 있다. 각 부품은 정수 형태의 고유한 번호가 있다. 어느 날 손님이 M개의 종류의 부품을 대량으로 구매하겠다며 당일 날 견적서를 요청했다. 동빈이는 때를 놓치지 않고 손님이 문의한 부품 M개의 종류를 모두 확인해서 견적서를 작성해야 한다. 이때 가게 안에 부품이 모두 있는지 확인하는 프로그램을 작성해 보자

## 입력조건

- 첫째 줄에 정수 N이 주어진다. (1<= N <= 1,000,000)
- 둘째 줄에는 공백으로 구분하여 N개의 정수가 주어진다. 이때 정수는 1보다 크고 1,000,000이하이다.
- 셋째 줄에는 정수 M이 주어진다. (1<= N <= 1,000,000)
- 넷째 줄에는 공백으로 구분하여 M개의 정수가 주어진다. 이때 정수는 1보다 크고 1,000,000이하이다.

## 출력조건

- 첫째 줄에 공백으로 구분하여 각 부품이 존재하면 yes, 없으면 no를 출력한다.

## 입력예시

5
8 3 7 9 2
3
5 7 9

## 출력예시

no yes yes

## 해설

### 이진 탐색

```python
def binary_search(array, target, start, end):
    while start <>= end:
        mid = (start + end) / 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 클 경우 오른쪽 확인
        else:
            start = mid +1
    return None

# N 가게의 부품수
n = int(input())
# 가게에 있는 전체 부품 번호를 공백으로 구분하여 입력
array = list(map(int,input().split()))
array.sort() # 이진 탐색을 위한 정렬
# M 손님이 요청한 부품의 개수
m = int(input())
# 손님이 요청한 전체 부품 번호를 공백으로 구분하여 입력
x = list(map(int,input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    result = binary_search(array, i, 0, n-1)
    if result != None:
        print('yes',end=' ')
    else:
        print('no',end=' ')
```

### 계수 정렬

```python
# N 가게의 부품 개수
n = int(input())
# 가능한 부품 개수만큼 배열 생성
array = [0] * 1000001
# 가게에 있는 전체 부품 번호를 입력 받아서 기록
for i in input().split():
    array[int(i)] = 1

# M 손님이 확인 요청한 부품 개수
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백으로 구분하여 입력
x = list(map(int,input().split))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if array[i] == 1:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

### 집합 자료형

```python
# n 가게의 부품 개수
n = int(input())
# 가게에 있는 전체 부품 번호를 입력 받아 집합(set) 자료형에 기록
array = set(map(int,input().split()))

# m 손님이 확인 요청한 부품 개수
m = int(input())
# 손님이 확인 요청한 전체 부품 번호
x = list(map(int, input().split()))

# 손님이 확인 요청한 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if i in array:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```
