# S최소생산비용

```python
def cost(i,N,sumV):
    global ans
    if sumV > ans:
        return
    if i == N:
        if ans > sumV:
            ans = sumV
            return ans

    for j in range(N):
        if visited[j] != 1:
            visited[j] = 1
            sumV += arr[i][j]
            cost(i+1,N,sumV)
            visited[j] = 0
            sumV -= arr[i][j]

for tc in range(int(input())):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    visited = [0] * N
    ans = 1e9
    cost(0,N,0)
    print(f'#{tc+1} {ans}')
```