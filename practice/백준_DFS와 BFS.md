# DFS와 BFS (1260)



## code

```python
from collections import deque

N, M, V = map(int,input().split())
graph = [[] for _ in range(N+1)]

for _ in range(M):
    x, y = map(int,input().split())
    graph[x].append(y)
    graph[y].append(x)

for lst in graph:
    lst.sort()

visited = [0]*(N+1)

# DFS
def dfs(graph, v, visited):
    visited[v] = 1
    print(v, end=' ')
    for i in graph[v]:
        if not visited[i]:
            dfs(graph, i, visited)

dfs(graph, V, visited)
print('')
visited = [0]*(N+1)

# BFS
def bfs(graph, v, visited):
    q = deque()
    q.append(v)
    visited[v] = 1

    while q:
        tmp = q.popleft()
        print(tmp, end=' ')
        for i in graph[tmp]:
            if not visited[i]:
                q.append(i)
                visited[i] = 1

bfs(graph, V, visited)
```

