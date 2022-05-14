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
def correct(p): # 올바른 문자열인지 검사(짝이 맞는지 체크)ㅡ스택활용
    stack = []
    for j in p:
        if j == '(':
            stack.append(j)
        elif j == ')':
            if stack:
                stack.pop()
            else: # 스택이 비어있다면 짝이 안맞는 것이므로 즉시 리턴
                return False
    if not stack: #스택이 완전히 비어있어야 올바른 문자열
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

