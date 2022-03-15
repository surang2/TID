# S노드의거리

```python
from collections import deque

for tc in range(int(input())):
    V, E = map(int, input().split())
    grid = [[0]*(V+1) for _ in range(V+1)]

    for i in range(0,E):
        a, b = map(int, input().split())
        grid[a][b] = 1
        grid[b][a] = 1

    S, G = map(int, input().split())
    queue = [S]
    visited = [0]*(V+1)
    visited[S] = 1
    queue = deque(queue)
    while visited[G] == 0 and queue:
        tmp = queue.popleft()
        for node in range(1, V+1):
            if grid[tmp][node] == 1 and visited[node] == 0:
                queue.append(node)
                visited[node] = visited[tmp] + 1

    if visited[G]:
        print(f'#{tc+1} {visited[G]-1}')
    else:
        print(f'#{tc+1} {visited[G]}')
```

