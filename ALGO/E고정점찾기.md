# E고정점

```python
N = int(input())
arr = list(map(int, input().split()))

start = 0
end = N-1
answer = -1 # 고정점이 없는경우를 생각해 -1로 값 초기화
while start <= end: # 찾아야 하는 값을 인덱스로 두고 이진탐색
    mid = (start + end) // 2
    if arr[mid] == mid:
        answer = mid
        break
    elif arr[mid] < mid:
        start = mid + 1
    else:
        end = mid - 1
print(answer)
```

