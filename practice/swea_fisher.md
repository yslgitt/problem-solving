## code

```python
import sys
sys.stdin = open("sample_input.txt")
import itertools

T = int(input())
for test_case in range(1,T+1):

    N = int(input())
    lst = [list(map(int,input().split())) for _ in range(3)]
    result = 10000000000

    a = list(itertools.permutations(lst, 3))
    for b in a:
        fish1 = [0] * (N+1)
        fish2 = [0] * (N+1)
        for i in range(3):
            gate = b[i][0]
            man = b[i][1]
            dx = [-1, 1]
            d = 0

            while man:
                if fish1[gate] == 0:
                    fish1[gate] = 1
                    man -= 1
                else:
                    nx = gate + dx[d%2]*(d//2+1)
                    if 0 < nx < N+1 and fish1[nx] == 0:
                        fish1[nx] = d//2+2
                        man -= 1
                    else:
                        d += 1
        sum1 = sum(fish1)
        for i in range(3):
            gate = b[i][0]
            man = b[i][1]
            dx = [1, -1]
            d = 0

            while man:
                if fish2[gate] == 0:
                    fish2[gate] = 1
                    man -= 1
                else:
                    nx = gate + dx[d%2]*(d//2+1)
                    if 0 < nx < N+1 and fish2[nx] == 0:
                        fish2[nx] = d//2+2
                        man -= 1
                    else:
                        d += 1
        sum2 = sum(fish2)
        S = min(sum1, sum2)
        result = min(S, result)

    print(f'#{test_case} {result}')
```

