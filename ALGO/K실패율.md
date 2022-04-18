# K.실패율

```python
def solution(N, stages):
    user = len(stages)
    level = 1
    tmp_answer = []
    while level <= N:
        if user:
            tmp = stages.count(level)/user
        else:
            tmp = 0
        tmp_answer.append((level, tmp))
        user -= stages.count(level)
        level += 1
    tmp_answer = sorted(tmp_answer, key=lambda x : (-x[1]))
    answer = []
    for i in tmp_answer:
        answer.append(i[0])
    return answer

################## 밑에는 딕셔너리 사용###########################


def solution(N, stages):
    user = len(stages)
    level = 1
    tmp_answer = {}
    while level <= N:
        if user:
            tmp = stages.count(level)/user
            tmp_answer[level] = tmp
            user -= stages.count(level)
        else:
            tmp_answer[level] = 0
        level += 1
    answer = list(map(lambda x : x[0], reversed(sorted(tmp_answer.items(), key = lambda x : (x[1], -x[0])))))
    return answer



```

