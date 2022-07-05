# 동물원



## code

```python
N = int(input())

dp = [3, 7]

for i in range(2, N):
    dp.append((dp[i-2]+2*dp[i-1])%9901)

print(dp[N-1])
```



## error

```python
N = int(input())

dp = [3, 7]

for i in range(2, N):
    dp.append(dp[i-2]+2*dp[i-1])

print(dp[N-1]%9901)
```

