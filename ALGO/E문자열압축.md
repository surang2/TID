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
                if cnt > 1: # 단위 길이로 검사했을 때, 다음에 오는 값이 다른 경우에 이전까지의 값을 압축해서 문자열에 저장
                    char += str(cnt) + s[j:j+i]
                else:
                    char += s[j:j+i]
                cnt = 1

        tmp = len(char)
        if answer > tmp:
            answer = tmp
    return answer
```

