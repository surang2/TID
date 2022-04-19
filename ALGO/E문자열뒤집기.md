# E문자열뒤집기

```python
S = list(input())
start = S[0] # 첫 문자열이 무엇인지 체크
cnt = 0
# 주어진 문자열이 첫 문자열과 다르고, 직전 문자열과도 다른 경우에 카운트 해줌(문자를 한꺼번에 뒤집을 수 있으므로)
for i in range(1, len(S)):
    if S[i] != start and S[i] != S[i-1]:
        cnt += 1
print(cnt)
```