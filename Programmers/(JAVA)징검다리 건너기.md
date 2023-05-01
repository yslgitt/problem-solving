# 💚 징검다리 건너기

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/64062



#### 💁‍♀️ 문제 설명

카카오 초등학교의 "니니즈 친구들"이 "라이언" 선생님과 함께 가을 소풍을 가는 중에 **징검다리**가 있는 개울을 만나서 건너편으로 건너려고 합니다. "라이언" 선생님은 "니니즈 친구들"이 무사히 징검다리를 건널 수 있도록 다음과 같이 규칙을 만들었습니다.

- 징검다리는 일렬로 놓여 있고 각 징검다리의 디딤돌에는 모두 숫자가 적혀 있으며 디딤돌의 숫자는 한 번 밟을 때마다 1씩 줄어듭니다.
- 디딤돌의 숫자가 0이 되면 더 이상 밟을 수 없으며 이때는 그 다음 디딤돌로 한번에 여러 칸을 건너 뛸 수 있습니다.
- 단, 다음으로 밟을 수 있는 디딤돌이 여러 개인 경우 무조건 가장 가까운 디딤돌로만 건너뛸 수 있습니다.

"니니즈 친구들"은 개울의 왼쪽에 있으며, 개울의 오른쪽 건너편에 도착해야 징검다리를 건넌 것으로 인정합니다.
"니니즈 친구들"은 한 번에 한 명씩 징검다리를 건너야 하며, 한 친구가 징검다리를 모두 건넌 후에 그 다음 친구가 건너기 시작합니다.

디딤돌에 적힌 숫자가 순서대로 담긴 배열 stones와 한 번에 건너뛸 수 있는 디딤돌의 최대 칸수 k가 매개변수로 주어질 때, 최대 몇 명까지 징검다리를 건널 수 있는지 return 하도록 solution 함수를 완성해주세요.



----



#### 🤸‍♂️ 문제 해결

```java
import java.util.*;

class Solution {
    public int solution(int[] stones, int k) {
        
        Deque <Integer> q = new ArrayDeque<>();
        q.add(0);
        
        for (int i = 1; i < k; i++) {
            while (!q.isEmpty()){
                // 현재 상태서 더 큰 수가 오면 비우기
                if (stones[q.peek()] < stones[i]) q.clear();
                // 작은 아이들 삭제
                else if (stones[q.peekLast()] < stones[i]) q.pollLast();
                else break;
            }
            q.add(i);
        }
        
        int answer = stones[q.peek()];
        for (int i = k; i < stones.length; i++){
            if (q.peek() <= i-k) q.poll();
            
            while (!q.isEmpty()){
                if (stones[q.peek()] < stones[i]) q.clear();
                else if (stones[q.peekLast()] < stones[i]) q.pollLast();
                else break;
            }
            
            q.add(i);
            if (stones[q.peek()] < answer) answer = stones[q.peek()];
        }

        return answer;
    }
}
```





#### 🗨 다른 사람 풀이

```java
class Solution {
    public int solution(int[] stones, int k) {
        int left = 1, right = 1 << 30, max = 0;
        while(left <= right){
            int mid = (left / 2) + (right / 2), cnt = 0;
            for(int i : stones) {
                cnt = (i - mid) < 0 ? cnt + 1 : 0;
                if(cnt == k) break;
            }
            if(cnt < k) {
                left = mid + 1;
                max = Math.max(max, mid);
            }
            else right = mid - 1;
        }
        return max;
    }
}
```

- 이진탐색으로도 풀이 가능!
