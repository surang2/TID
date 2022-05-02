# E특정거리의도시찾기

```python
from collections import deque
N, M, K, X = map(int, input().split())
graph = [[] for _ in range(N+1)]
for i in range(M):
    a, b = map(int, input().split())
    graph[a].append(b) # 도시 간 연결관계 표시
visited = [0] * (N+1)
answer_list = []

q = deque()
q.append(X)
visited[X] = 1
while q:
    a = q.popleft()
    for j in graph[a]:
        if not visited[j]:
            q.append(j)
            visited[j] = visited[a]+1 # 출발도시까지의 거리에 + 1 해주면 해당 도시까지의 거리

for k in range(len(visited)):
    if visited[k] == K+1:
        answer_list.append(k)
if answer_list:
    for l in range(len(answer_list)):
        print(answer_list[l])
else:
    print(-1)
```

