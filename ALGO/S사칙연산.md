# S사칙연산.

```python
for tc in range(10):
    N = int(input())
    tree = [0]*(N+1)
    for i in range(N):
        tmp = list(input().split())
        if tmp[1] in ['+', '-', '*', '/']:
            tree[int(tmp[0])] = (tmp[1],int(tmp[2]),int(tmp[3]))
        else:
            tree[int(tmp[0])] = int(tmp[1])

    for i in range(N,0,-1):
        if type(tree[i]) is not int:
            if tree[i][0] == '+':
                tree[i] = tree[tree[i][1]] + tree[tree[i][2]]
            elif tree[i][0] == '-':
                tree[i] = tree[tree[i][1]] - tree[tree[i][2]]
            elif tree[i][0] == '*':
                tree[i] = tree[tree[i][1]] * tree[tree[i][2]]
            else:
                tree[i] = tree[tree[i][1]] / tree[tree[i][2]]

    print(f'#{tc+1} {int(tree[1])}')
```