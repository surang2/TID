# E볼링공고르기
```python
from itertools import combinations

N, M = map(int, input().split())
ball = list(map(int, input().split()))
case = combinations(ball,2)
cnt = 0
# 조합 모듈을 이용해서 가능한 조합을 구하고 두 공의 무게가 다른경우에만 카운트함
for i in case:
    if i[0] != i[1]:
        cnt += 1
print(cnt)
```