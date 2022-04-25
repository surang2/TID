# E럭키스트레이트

```python
N = input() # iterable 한 상태로 사용하기 위해 문자열로 받은 후
a, b = 0, 0
for i in range(0, len(N)//2): # for 문을 돌며 각각 더해주어
    a += int(N[i])
    b += int(N[i+(len(N)//2)])

if a == b: # 같은 값인지 확인한다
    print('LUCKY')
else:
    print('READY')
```

