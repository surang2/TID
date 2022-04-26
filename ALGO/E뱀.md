# E뱀
```python
from collections import deque
N = int(input())
arr = list([0]*N for _ in range(N))
K = int(input())
for k in range(K):
    x, y = map(int, input().split())
    arr[x-1][y-1] = 1

di = [0, 1, 0, -1]
dj = [1, 0, -1, 0]
d = 0
tails = deque()
direction = []
T = int(input())
for _ in range(T):
    t, s = input().split()
    t = int(t)
    direction.append((t,s))

time = 0
change = 0
i, j = 0, 0
bp = 0

while True:
    if time != direction[change][0]:
        ni = i + di[d]
        nj = j + dj[d]
        if 0 <= ni < N and 0 <= nj < N and (ni,nj) not in tails:
            if arr[i][j] == 0:
                tails.append((i, j))
                tmp = tails.popleft()

            else:
                arr[i][j] = 0
                tails.append((i,j))

            i, j = ni, nj
            time += 1
        else:
            bp = -1
    else:

        if direction[change][1] == 'L':
            d = (d + 3) % 4

        else:
            d = (d + 1) % 4
        if change < T-1:
            change += 1
        ni = i + di[d]
        nj = j + dj[d]

        ni = i + di[d]
        nj = j + dj[d]
        if 0 <= ni < N and 0 <= nj < N and (ni, nj) not in tails:
            if arr[i][j] == 0:
                tails.append((i, j))
                tmp = tails.popleft()

            else:
                arr[i][j] = 0
                tails.append((i, j))

            i, j = ni, nj
            time += 1
        else:
            break

    if bp == -1:
        break
print(time+1)
```

