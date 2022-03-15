# S회전문제

```python
from collections import deque
for tc in range(int(input())):
    N, M = map(int, input().split())
    lst = list(map(int, input().split()))
    d_lst = deque(lst)

    for i in range(M):
        tmp = d_lst.popleft()
        d_lst.append(tmp)

    print(f'#{tc+1} {d_lst[0]}')
```