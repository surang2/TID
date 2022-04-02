# S이진힙

```python
for tc in range(int(input())):
    N = int(input())
    arr = list(map(int, input().split()))
    tree = [0] # 인덱스를 맞춰주기 위해 0으로 시작
    for i in arr: # input을 하나하나 트리에 넣어가며 이진 최소힙 정렬 수행
        tree.append(i)
        C = len(tree)-1 # C는 인덱스로 사용할 예정이므로 -1해준다
        while C > 1:
            P = C // 2 # 부모 노드의 인덱스 도출
            if tree[P] > tree[C]:
                tree[P], tree[C] = tree[C], tree[P]
            C = C // 2 # 더 위의 조상 노드도 체크

    ans = 0
    while N > 1: # 조상 노드들의 합을 구하는 과정
        P = N // 2
        ans += tree[P]
        N = N // 2
    print(f'#{tc+1} {ans}')
```