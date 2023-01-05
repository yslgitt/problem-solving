# 💚 (SQL) 카테고리 별 상품 개수 구하기

[📝 문제링크]: https://school.programmers.co.kr/learn/courses/30/lessons/13152



#### 💁‍♀️ 문제 설명

다음은 어느 의류 쇼핑몰에서 판매중인 상품들의 정보를 담은 `PRODUCT` 테이블입니다. `PRODUCT` 테이블은 아래와 같은 구조로 되어있으며, `PRODUCT_ID`, `PRODUCT_CODE`, `PRICE`는 각각 상품 ID, 상품코드, 판매가를 나타냅니다.

| Column name  | Type       | Nullable |
| ------------ | ---------- | -------- |
| PRODUCT_ID   | INTEGER    | FALSE    |
| PRODUCT_CODE | VARCHAR(8) | FALSE    |
| PRICE        | INTEGER    | FALSE    |

상품 별로 중복되지 않는 8자리 상품코드 값을 가지며, 앞 2자리는 카테고리 코드를 의미합니다.



##### 문제

`PRODUCT` 테이블에서 상품 카테고리 코드(`PRODUCT_CODE` 앞 2자리) 별 상품 개수를 출력하는 SQL문을 작성해주세요. 결과는 상품 카테고리 코드를 기준으로 오름차순 정렬해주세요.



##### 예시

예를 들어 `PRODUCT` 테이블이 다음과 같다면

| PRODUCT_ID | PRODUCT_CODE | PRICE |
| ---------- | ------------ | ----- |
| 1          | A1000011     | 10000 |
| 2          | A1000045     | 9000  |
| 3          | C3000002     | 22000 |
| 4          | C3000006     | 15000 |
| 5          | C3000010     | 30000 |
| 6          | K1000023     | 17000 |

상품 카테고리 코드 별 상품은 아래와 같으므로,

- `A1`: `PRODUCT_ID`가 1, 2 인 상품
- `C3`: `PRODUCT_ID`가 3, 4, 5 인 상품
- `K1`: `PRODUCT_ID`가 6 인 상품

다음과 같은 결과가 나와야 합니다.

| CATEGORY | PRODUCTS |
| -------- | -------- |
| A1       | 2        |
| C3       | 3        |
| K1       | 1        |



----



#### 🤸‍♂️ 문제 해결

```mysql
SELECT LEFT(PRODUCT_CODE, 2) AS CATEGORY, COUNT(*) AS PRODUCTS
FROM PRODUCT
GROUP BY CATEGORY
```



#### ✏ NOTE

- **MySQL** 

  - LEFT : 문자에 왼쪽을 기준으로 일정 개수를 가져오는 함수.
  - MID : 문자에 지정한 시작 위치를 기준으로 일정 개수를 가져오는 함수.
  - RIGHT : 문자에 오른쪽을 기준으로 일정 개수를 가져오는 함수.

  〰

  ```mysql
  SELECT LEFT('abcdefg', 3); -- abc
  
  SELECT MID('abcdefg', 2, 4); -- bcde
  -- SELECT SUBSTR('abcdefg', 2, 4);
  -- SELECT SUBSTRING('abcdefg', 2, 4); 
  
  SELECT RIGHT('abcdefg', 3); -- efg
  ```

  

- **Oracle**

  ORACLE 내장함수에는 LEFT(), RIGHT() 함수가 없음.

  **substr** 함수를 통해 똑같이 구현이 가능하다.

  〰

  ```sql
  SELECT SUBSTR('Hello, World!', 7) -- World!
  
  SELECT SUBSTR('Hello, World!', 1, 4) -- Hell
  
  SELECT SUBSTR('Hello, World!', -4) -- >> rld!
  ```

  

 