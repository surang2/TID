# K비밀지도
```python
def solution(n, arr1, arr2):
    answer = []
    for i in range(n):
        tmp1 = format(arr1[i], 'b') # format 함수를 통해 2진수 변환 o는 8진수 x는 16
        while n > len(tmp1):
            tmp1 = '0' + tmp1
        tmp2 = format(arr2[i], 'b')
        while n > len(tmp2):
            tmp2 = '0' + tmp2

        key = ''
        for j in range(n):
            if tmp1[j] == '0' and tmp2[j] == '0':
                key += ' '
            else:
                key += '#'
        answer.append(key)
    return answer
```

