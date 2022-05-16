# K다트게임

```python
def solution(dartResult): # 걸림
    cal = []
    score = []
    n = 0
    while n < len(dartResult)-1: # 점수와 식으로 문자열 분리
        if dartResult[n] in ['S', 'D', 'T']:
            if dartResult[n+1] in ['*', '#']:
                cal.append(dartResult[n:n + 2]) #문자열 두개를 한번에 식으로 처리
                n += 2
            else:
                cal.append(dartResult[n])
                n += 1
        else:
            if dartResult[n+1] in ['S', 'D', 'T', '*', '#']:
                score.append(int(dartResult[n]))
                n += 1
            else:
                score.append(int(dartResult[n:n+2]))
                n += 2
    if dartResult[-1] in ['S', 'D', 'T']: # 문자열의 마지막에 *, # 옵션이 안붙는경우
        cal.append(dartResult[-1])

    answer = 0
    tmp = 0
    for i in range(3): # 하드코딩 #tmp 변수를 통해 이전의 점수를 기억
        if cal[i] == 'S':
            answer += score[i]
            tmp = score[i]
        elif cal[i] == 'D':
            answer += score[i]**2
            tmp = score[i]**2
        elif cal[i] == 'T':
            answer += score[i]**3
            tmp = score[i]**3
        elif cal[i] == 'S*':
            answer += score[i]*2
            answer += tmp
            tmp = score[i]*2
        elif cal[i] == 'D*':
            answer += score[i]**2 * 2
            answer += tmp
            tmp = score[i]**2 * 2
        elif cal[i] == 'T*':
            answer += score[i] ** 3 * 2
            answer += tmp
            tmp = score[i] ** 3 * 2
        elif cal[i] == 'S#':
            answer += -score[i]
            tmp = -score[i]
        elif cal[i] == 'D#':
            answer += -score[i]**2
            tmp = -score[i]**2
        elif cal[i] == 'T#':
            answer += -score[i]**3
            tmp = -score[i]**3
    return answer
```

