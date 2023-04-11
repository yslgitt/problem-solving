# 💚 달리기 경주

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/178871



#### 💁‍♀️ 문제 설명

얀에서는 매년 달리기 경주가 열립니다. 해설진들은 선수들이 자기 바로 앞의 선수를 추월할 때 추월한 선수의 이름을 부릅니다. 예를 들어 1등부터 3등까지 "mumu", "soe", "poe" 선수들이 순서대로 달리고 있을 때, 해설진이 "soe"선수를 불렀다면 2등인 "soe" 선수가 1등인 "mumu" 선수를 추월했다는 것입니다. 즉 "soe" 선수가 1등, "mumu" 선수가 2등으로 바뀝니다.

선수들의 이름이 1등부터 현재 등수 순서대로 담긴 문자열 배열 `players`와 해설진이 부른 이름을 담은 문자열 배열 `callings`가 매개변수로 주어질 때, 경주가 끝났을 때 선수들의 이름을 1등부터 등수 순서대로 배열에 담아 return 하는 solution 함수를 완성해주세요.





----



#### 🤸‍♂️ 문제 해결

```java
import java.util.*;

class Solution {
    public String[] solution(String[] players, String[] callings) {
        Map <String, Integer> map = new HashMap();
        String[] answer = players;
        for (int i = 0; i < players.length; i++) {
            map.put(players[i], i);
        }
        
        for (int i = 0; i < callings.length; i++) {
            int idx = map.get(callings[i]);
            answer[idx] = answer[idx-1];
            answer[idx-1] = callings[i];
            map.put(callings[i], idx - 1);
            map.put(answer[idx], idx); 
            }
        
        return answer;
    }
}
```

