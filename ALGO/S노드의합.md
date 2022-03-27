# S노드의합

```python
for tc in range(int(input())):
    N, M, L = map(int, input().split()) #N은 노드의 수, M은 리프노드 개수, L은 출력할 노드번호
    tree = [0]*(N+1)
    for i in range(M):
        Idx, Number = map(int, input().split())
        tree[Idx] = Number

    for i in range(len(tree)):
        if tree[i] != 0:
            p = i-1
            break

    while tree[1] == 0:
        if p*2+1 <= len(tree)-1:
            tree[p] = tree[p*2] + tree[p*2+1]
        else:
            tree[p] = tree[p*2]
        p -= 1
    print(f'#{tc+1} {tree[L]}')
```

