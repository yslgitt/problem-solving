# 💚 뒤에 있는 큰 수 찾기

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/154539



#### 💁‍♀️ 문제 설명

정수로 이루어진 배열 `numbers`가 있습니다. 배열 의 각 원소들에 대해 자신보다 뒤에 있는 숫자 중에서 자신보다 크면서 가장 가까이 있는 수를 뒷 큰수라고 합니다.
정수 배열 `numbers`가 매개변수로 주어질 때, 모든 원소에 대한 뒷 큰수들을 차례로 담은 배열을 return 하도록 solution 함수를 완성해주세요. 단, 뒷 큰수가 존재하지 않는 원소는 -1을 담습니다.



----



#### 🤸‍♂️ 문제 해결

```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        int n = numbers.length;
        int[] answer = new int[n];
    
        Stack <Integer> stack = new Stack();
        answer[n-1] = -1;
        stack.push(numbers[n-1]);
        
        for (int i = n-2; i >= 0; i--){
            while(!stack.empty()){
                int k = stack.pop();
                
                if (k > numbers[i]) {
                    answer[i] = k;
                    stack.push(k);
                    stack.push(numbers[i]);
                    break;
                }
            }
            
            if (stack.empty()){
                stack.push(numbers[i]);
                answer[i] = -1;
            }
        } 
        
        return answer;   
    }
}
```

