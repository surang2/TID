# Scontact

```python
from collections import deque
for tc in range(10):
    N, S = map(int, input().split())
    lst = list(map(int, input().split()))
    grid = [[0]*101 for _ in range(101)]
    for i in range(0,len(lst),2):
        a, b = lst[i], lst[i+1]
        grid[a][b] = 1

    que = deque()
    contacted = [0]*101

    que.append(S)
    contacted[S] = 1
    ans = S
    while que:
        g = que.popleft()
        if contacted[ans] < contacted[g] or contacted[ans] == contacted[g] and ans < g:
            ans = g

        for i in range(101):
            if grid[g][i] == 1 and contacted[i] == 0:
                que.append(i)
                contacted[i] = contacted[g] + 1

    print(f'#{tc+1} {ans}')
```