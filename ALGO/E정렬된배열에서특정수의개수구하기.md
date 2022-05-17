# E정렬된배열에서특정수의개수구하기

```python
N, x = map(int, input().split())
arr = list(map(int, input().split()))

start = 0
end = N-1
right, left = 0, 2 # x 값이 없을 경우
while start <= end: # x 숫자가 등장하는 오른쪽 인덱스 찾기
    mid = (start + end) // 2
    if arr[mid] == x:
        right = mid
        start = mid + 1
    elif arr[mid] < x:
        start = mid + 1
    else:
        end = mid - 1

start = 0 # 시작, 끝 인덱스 초기화
end = N-1

while start <= end: # x 숫자가 등장하는 왼쪽 인덱스 찾기
    mid = (start + end) // 2
    if arr[mid] == x:
        left = mid
        end = mid - 1
    elif arr[mid] < x:
        start = mid + 1
    else:
        end = mid - 1

print(right-left+1)

```

