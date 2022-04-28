# E문자열압축

```python
def solution(s):
    answer = len(s)

    for i in range(1,len(s)//2+1): # 압축 단위 길이 설정
        char = ''
        cnt = 1

        for j in range(0, len(s), i):
            if s[j:j+i] == s[j+i:j+2*i]:
                cnt += 1
            else:
                if cnt > 1:
                    char += str(cnt) + s[j:j+i]
                else:
                    char += s[j:j+i]
                cnt = 1

        tmp = len(char)
        if answer > tmp:
            answer = tmp
    return answer
```

