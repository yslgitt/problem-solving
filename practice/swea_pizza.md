# 피자 굽기



## code

```python
from collections import deque
 
T = int(input())
for test_case in range(1,T+1):
    N, P = map(int,input().split())
    cheeze = list(enumerate(map(int,input().split())))
 
    Q = deque(cheeze[:N])
    cheeze = deque(cheeze[N:])
 
    while len(Q) > 1:
        while len(Q) < N and cheeze:
            Q.append(cheeze.popleft())
        idx, cz = Q.popleft()
        if cz > 1:
            Q.append((idx, cz//2))
         
    print(f'#{test_case} {Q[0][0]+1}')

```

