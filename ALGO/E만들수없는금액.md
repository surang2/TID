# E만들수없는금액
```python
from itertools import product
N = int(input())
coin = list(map(int, input().split()))
sumV_lst = []
# 중복 가능한 순열을 사용해 가능한 부분집합 쌍을 만들고 부분집합의 합 계산하여 리스트에 저장
for i in product(range(2), repeat=N):
    sumV = 0
    for j in range(N):
        if i[j] == 1:
            sumV += coin[j]
    sumV_lst.append(sumV)
sumV_lst = set(sumV_lst)
sumV_lst = list(sumV_lst)
sumV_lst.sort() # 오름차순 정렬

ans = 1
i = 0
while True: # 숫자를 1씩 증가시켜가며 해당 숫자가 리스트 안에 있는지 확인하고, 없으면 그 값이 최솟값이므로 while문 종료
    if ans == sumV_lst[i]:
        ans += 1
    else:
        if ans > sumV_lst[i]:
            if i < len(sumV_lst)-1:
                i += 1
            else:
                break
        else:
            break
print(ans)
```