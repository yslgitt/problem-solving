# 섬의 개수 (백준: 4963)



## code

```python
dx = [0, -1, -1, -1, 0, 1, 1, 1]
dy = [1, 1, 0, -1, -1, -1, 0, 1]

while 1:
    w, h = map(int,input().split())
    if w == 0 and h == 0: # 끝나는 조건
        break

    M = [list(map(int,input().split())) for _ in range(h)]
    visited = [[0]*w for _ in range(h)]
    q = []
    cnt = 0

    for i in range(h):
        for j in range(w):
            if M[i][j] == 1 and not visited[i][j]: 
                q.append((i,j))
                visited[i][j] = 1

                while q:
                    tx, ty = q.pop(0)
                    for d in range(8):
                        nx = tx + dx[d]
                        ny = ty + dy[d]

                        if 0 <= nx < h and 0 <= ny < w and not visited[nx][ny] and M[nx][ny]:
                            q.append((nx,ny))
                            visited[nx][ny] = 1

                cnt += 1
    print(cnt)
```





## error

`if M[i][j] == 1 and not visited[i][j]:`  방문 했던 곳을 제외하지 않아 중복 카운트가 생김..