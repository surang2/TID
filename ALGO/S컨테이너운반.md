# S컨테이너운반

```python
for tc in range(int(input())):
    N, M = map(int, input().split())
    Weight = sorted(list(map(int,input().split()))) # sort 메서드가 안써져서
    Capacity = sorted((map(int,input().split())))
    Weight = Weight[::-1]
    Capacity = Capacity[::-1]
    ans = 0
    for i in range(N):
        for j in range(M):
            if Weight[i] <= Capacity[j]:
                ans += Weight[i]
                Capacity.pop(0)
                M -= 1
                break
    print(f'#{tc+1} {ans}')
```