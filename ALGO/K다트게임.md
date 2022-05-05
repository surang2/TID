# K다트게임

```python
def solution(dartResult): # 걸림
    cal = []
    score = []
    n = 0
    while n < len(dartResult)-1:
        if dartResult[n] in ['S', 'D', 'T']:
            if dartResult[n+1] in ['*', '#']:
                cal.append(dartResult[n:n + 2])
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
    if dartResult[-1] in ['S', 'D', 'T']:
        cal.append(dartResult[-1])

    answer = 0
    tmp = 0
    for i in range(3): # 하드코딩
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

