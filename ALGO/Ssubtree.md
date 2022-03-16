# Ssubtree

```python
for tc in range(int(input())):
    E, N = map(int, input().split())
    lst = list(map(int, input().split()))
    tree = [[0]*2 for _ in range(E+2)]
    for i in range(0,len(lst),2):
        p = lst[i]
        c = lst[i+1]
        if tree[p][0] == 0:
            tree[p][0] = c
        else:
            tree[p][1] = c
    cnt = 0
    def preorder(root):
        if root:
            global cnt
            cnt += 1
            preorder(tree[root][0])
            preorder(tree[root][1])
    preorder(N)
    print(f'#{tc+1} {cnt}')
```