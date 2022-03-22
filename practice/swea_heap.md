# 이진 힙



## code

```python
T = int(input())
for test_case in range(1,T+1):
    N = int(input())
    tree = [0]*(N+1)
    nums = [0] + list(map(int,input().split()))
    for i in range(1,N+1):
        tree[i] = nums[i]
        while i > 1:
            if tree[i] < tree[i//2]:
                tree[i], tree[i//2] = tree[i//2], tree[i]
            i = i//2

    result = 0
    while N >= 1:
        N = N // 2
        result += tree[N]


    print(f'#{test_case} {result})
```

