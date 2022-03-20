# subtree



## code

```python
def pre_order(root):
    global cnt
    if c1[root]:
        cnt += 1
        pre_order(c1[root])
    if c2[root]:
        cnt += 1
        pre_order(c2[root])
         
 
T = int(input())
for test_case in range(1,T+1):
    E, sub = map(int,input().split())
    tree = list(map(int,input().split()))
    c1 = [0]*(E+2)
    c2 = [0]*(E+2)
    for i in range(0, len(tree), 2):
        if c1[tree[i]] == 0:
            c1[tree[i]] = tree[i+1]
        else:
            c2[tree[i]] = tree[i+1]
 
    cnt = 1
    pre_order(sub)
     
    print(f'#{test_case} {cnt}')

```

