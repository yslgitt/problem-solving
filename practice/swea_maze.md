# 미로



## code

```python
from collections import deque
dx = [1, 0, 0, -1]
dy = [0, 1, -1, 0]

for test_case in range(1,11):
    tc = int(input())
    maze = [list(map(int,input())) for _ in range(16)]
    result = 0

    Q = deque([])
    for i in range(0,16):
        for j in range(0,16):
            if maze[i][j] == 2:
                Q.append((i,j))
                maze[i][j] = 1

    while Q:
        x,y = Q.popleft()

        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]

            if 0 <= nx < 16 and 0 <= ny < 16 and maze[nx][ny] != 1:
                if maze[nx][ny] == 3:
                    result = 1
                    break

                maze[nx][ny] = 1
                Q.append((nx,ny))

        if result == 1:
            break

    print(f'#{test_case} {result}')

```

