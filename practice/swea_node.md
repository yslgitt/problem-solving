# 노드의 합



## code

```python
T = int(input())
for test_case in range(1,T+1):
    N, M, L = map(int,input().split())
    nodes = [0]*(N+1)

    for _ in range(M):
        a, b = map(int,input().split())
        nodes[a] = b

    for i in range(N, 0, -1):
        if nodes[i] == 0:
            if i*2 == N:
                nodes[i] = nodes[i*2]
            else:
                nodes[i] = nodes[i*2] + nodes[i*2 +1]


    print(f'#{test_case} {nodes[L]}')
```

