# E연구소

```python
from itertools import combinations
from collections import deque
from copy import deepcopy

N, M = map(int, input().split())
arr = [list(map(int, input().split())) for _ in range(N)]
space_list = []
di = [0,1,0,-1]
dj = [1,0,-1,0]
tmp = 0

def BFS():
    q = deque()
    for i in range(N):
        for j in range(M):
            if arr[i][j] == 2:
                q.append((i,j))
                while q:
                    ci,cj = q.popleft()
                    for d in range(4):
                        ni = ci + di[d]
                        nj = cj + dj[d]
                        if 0 <= ni < N and 0 <= nj < M and tmp_arr[ni][nj] == 0:
                            tmp_arr[ni][nj] = 2
                            q.append((ni,nj))

for i in range(N): # 벽이 세워질 수 있는 좌표 탐색
    for j in range(M):
        if arr[i][j] == 0:
            space_list.append(tmp)
        tmp += 1

wall_list = list(combinations(space_list,3)) # 3개 벽 좌표 경우의 수 생성

answer = 0
for walls in wall_list: # for문 돌면서 해당 좌표에 벽 세우고 BFS실행
    tmp_arr = deepcopy(arr) 
    for wall in walls:
        tmp_arr[wall // M][wall % M] = 1 

    BFS()
    save = 0
    for x in range(N):
        for y in range(M):
            if tmp_arr[x][y] == 0:
                save += 1
    if answer < save:
        answer = save
print(answer)
```

