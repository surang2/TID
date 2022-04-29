```python
def solution(n, arr1, arr2):
    answer = []
    for i in range(n):
        tmp1 = format(arr1[i], 'b')
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

