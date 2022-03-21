# S정사각형방

```python
for tc in range(int(input())):
    from collections import deque
    N = int(input())
    grid = [list(map(int, input().split())) for _ in range(N)]
    visited = [[0]*N for _ in range(N)]
    di = [0, 1, 0, -1]
    dj = [1, 0, -1, 0]
    min_num = N**2
    cnt = 0
    for i in range(N):
        for j in range(N):
            if visited[i][j] == 0:
                que = deque()
                visited = [[0] * N for _ in range(N)]
                que.append((i,j))
                visited[i][j] = 1
                ans = [grid[i][j]]
                while que:
                    ci, cj = que.popleft()
                    for d in range(4):
                        ni = ci + di[d]
                        nj = cj + dj[d]
                        if 0 <= ni < N and 0 <= nj < N and visited[ni][nj] == 0 and abs(grid[ci][cj] - grid[ni][nj]) == 1:
                            que.append((ni,nj))
                            visited[ni][nj] = 1
                            ans.append(grid[ni][nj])
                num, long = min(ans), len(ans)
                if cnt < long or cnt == long and min_num > num:
                    cnt = long
                    min_num = num
    print(f'#{tc+1} {min_num} {cnt}')
```