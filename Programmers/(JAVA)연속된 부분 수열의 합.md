# 💚 연속된 부분 수열의 합

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/178870



#### 💁‍♀️ 문제 설명

비내림차순으로 정렬된 수열이 주어질 때, 다음 조건을 만족하는 부분 수열을 찾으려고 합니다.

- 기존 수열에서 임의의 두 인덱스의 원소와 그 사이의 원소를 모두 포함하는 부분 수열이어야 합니다.
- 부분 수열의 합은 `k`입니다.
- 합이 `k`인 부분 수열이 여러 개인 경우 길이가 짧은 수열을 찾습니다.
- 길이가 짧은 수열이 여러 개인 경우 앞쪽(시작 인덱스가 작은)에 나오는 수열을 찾습니다.

수열을 나타내는 정수 배열 `sequence`와 부분 수열의 합을 나타내는 정수 `k`가 매개변수로 주어질 때, 위 조건을 만족하는 부분 수열의 시작 인덱스와 마지막 인덱스를 배열에 담아 return 하는 solution 함수를 완성해주세요. 이때 수열의 인덱스는 0부터 시작합니다.





----



#### 🤸‍♂️ 문제 해결

```java
class Solution {
    public int[] solution(int[] sequence, int k) {
        int n = sequence.length;
        
        int now = sequence[0];
        
        int l = 0; int r = 0;
        int al = 0; int ar = 0;
        
        int min = Integer.MAX_VALUE;
        while (true) {
            if (now == k) {
                if (r - l < min) {
                    min = r - l;
                    al = l; ar = r;
                    if (min == 0) break;
                }
                l++; r++;
                if (r == n) break;
                now = now + sequence[r] - sequence[l-1];
                
            } else if (now > k) {
                now -= sequence[l];
                l++;
            
            } else if (now < k) {
                r++;
                if (r == n) break;
                now += sequence[r];
                
            }
        }
        int[] answer = new int [] {al,ar};
        return answer;
    }
}
```

