# K신규아이디추천

```python
def solution(new_id):
    cnt = 1 # 수정 사항 체크 변수
    while cnt > 0:
        cnt = 0
        # 1단계 소문자 치환
        new_id = new_id.lower()

        # 2단계 특수문자 제거
        char = 'abcdefghijklmnopqrstuvwxyz0123456789-_.'
        tmp = list(new_id)

        for i in range(len(tmp)):
            if tmp[i] not in char:
                tmp[i] = ''
                cnt += 1
        new_id = ''.join(tmp)

        # 3단계 .연속일시 제거
        tmp = list(new_id)
        for i in range(len(new_id) - 1):
            if tmp[i] == tmp[i + 1] == '.':
                tmp[i] = ''
                cnt += 1
        new_id = ''.join(tmp)

        # 4단계 .로 시작하거나 끝난다면 제거
        if new_id[0] == '.':
            new_id = new_id[1:]
            cnt += 1
        if new_id != '':
            if new_id[-1] == '.':
                new_id = new_id[:-1]
                cnt += 1

        # 5단계 id가 빈문자열이라면 a 대입
        if new_id == '':
            new_id = 'a'
            cnt += 1

        # 6단계 16글자 이상이면 15글자까지 잘라냄
        if len(new_id) >= 16:
            new_id = new_id[:15]
            cnt += 1

        # 7단계 2글자 이하면 3글자 될때까지 마지막문자 반복
        if len(new_id) <= 2:
            while len(new_id) < 3:
                new_id += new_id[-1]
            cnt += 1

    answer = new_id
    return answer
```