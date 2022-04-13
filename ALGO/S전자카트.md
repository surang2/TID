# S전자카트

```python
from itertools import permutations

for tc in range(int(input())):
    N = int(input())
    arr = [[0]*(N+1)]+ [[0]+list(map(int, input().split())) for _ in range(N)]
    cost = 10000000
    for i in permutations(range(2,N+1)):
        tmp = 0
        for j in range(1,len(i)):
            tmp += arr[i[j-1]][i[j]]
        tmp += (arr[1][i[0]] + arr[i[-1]][1])
        if cost > tmp:
            cost = tmp
    print(f'#{tc+1} {cost}')
```