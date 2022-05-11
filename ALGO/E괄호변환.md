# E괄호변환

```python
def balance(p): # 균형잡힌 문자열인지 검사(갯수 체크)
    a, b = 0, 0
    for i in range(len(p)):
        if p[i] == '(':
            a += 1
        elif p[i] == ')':
            b += 1
        if a == b:
            return i
def correct(p): # 올바른 문자열인지 검사(짝이 맞는지 체크)
    stack = []
    for j in p:
        if j == '(':
            stack.append(j)
        elif j == ')':
            if stack:
                stack.pop()
            else:
                return False
    if not stack:
        return True
    else:
        return False

def solution(p): # 재귀적으로 함수 실행
    answer = ''
    if p == '':
        return answer
    i = balance(p)
    u = p[:i+1]
    v = p[i+1:]
    if correct(u):
        answer = u + solution(v)
    else:
        tmp = '('
        tmp += solution(v)
        tmp += ')'
        tmp_u = u[1:-1]
        u = ''
        for i in tmp_u:
            if i == '(':
                u += ')'
            else:
                u += '('
        answer = tmp + u
    return answer
```

