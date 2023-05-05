# 💚 공원 산책

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/172928



#### 💁‍♀️ 문제 설명

지나다니는 길을 'O', 장애물을 'X'로 나타낸 직사각형 격자 모양의 공원에서 로봇 강아지가 산책을 하려합니다. 산책은 로봇 강아지에 미리 입력된 명령에 따라 진행하며, 명령은 다음과 같은 형식으로 주어집니다.

- ["방향 거리", "방향 거리" … ]

예를 들어 "E 5"는 로봇 강아지가 현재 위치에서 동쪽으로 5칸 이동했다는 의미입니다. 로봇 강아지는 명령을 수행하기 전에 다음 두 가지를 먼저 확인합니다.

- 주어진 방향으로 이동할 때 공원을 벗어나는지 확인합니다.
- 주어진 방향으로 이동 중 장애물을 만나는지 확인합니다.

위 두 가지중 어느 하나라도 해당된다면, 로봇 강아지는 해당 명령을 무시하고 다음 명령을 수행합니다.
공원의 가로 길이가 W, 세로 길이가 H라고 할 때, 공원의 좌측 상단의 좌표는 (0, 0), 우측 하단의 좌표는 (H - 1, W - 1) 입니다.

![image](assets/217702316-1bd5d3ba-c1d7-4133-bfb5-36bdc85a08ba.png)

공원을 나타내는 문자열 배열 `park`, 로봇 강아지가 수행할 명령이 담긴 문자열 배열 `routes`가 매개변수로 주어질 때, 로봇 강아지가 모든 명령을 수행 후 놓인 위치를 [세로 방향 좌표, 가로 방향 좌표] 순으로 배열에 담아 return 하도록 solution 함수를 완성해주세요.



----



#### 🤸‍♂️ 문제 해결

```java
import java.util.*;

class Solution {
    public int[] solution(String[] park, String[] routes) {
        
        // 파크 정보 (파크 가로 크기, 세로 크기, 시작점)
        int H = park.length;
        int W = park[0].length();
        int [] now = new int [2];
        for (int i = 0; i < H; i++){
            for (int j = 0; j < W; j++){
                if (park[i].charAt(j) == 'S') {
                    now[0] = i;
                    now[1] = j;
                }
            }
        }
        
        
        // 한턴 씩 진행
        for (String turn : routes){
            String[] t = turn.split(" ");
            String d = t[0];
            int k = Integer.parseInt(t[1]);
            
            int ny = now[0]; int nx = now[1];
            int dy; int dx;
            // 방향 설정
            if (d.equals("N")){
                dy = -1; dx = 0;
            } else if (d.equals("S")){
                dy = 1; dx = 0;
            } else if (d.equals("W")) {
                dy = 0; dx = -1;
            } else {
                dy = 0; dx = 1;
            }
            
            // 한칸 씩 이동
            for (int i = 0; i < k; i++){
                ny += dy; nx += dx;
                // 조건 불합일 경우, 원래대로 
                if (ny < 0 || nx < 0 || ny >= H || nx >= W) {
                    ny = now[0]; nx = now[1]; 
                    break;
                }
                if (park[ny].charAt(nx) == 'X') {
                    ny = now[0]; nx = now[1];
                    break;
                }
            }        
            now[0] = ny;
            now[1] = nx;
        }
        
        return now;
    }
}
```





#### 🎹 참고

- 자바서 `" "` 와 `' '`의 차이 ⇒  **<u>`" "` 는 문자열(String),  `' '`은 문자(Char)</u>**
- `equals()`와 `==` 구분 
  - **`equals()`: 대상의 내용 자체 비교 메서드**
  - `==`: 주소값 비교 연산자
