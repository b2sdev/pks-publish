
## 순위 구하기 (ROW_NUMBER, RANK, DENSE_RANK 이해)

```sql
SELECT
    product_id
  , score
    -- score 순서로 유일한 순위를 붙임
  , ROW_NUMBER() OVER(ORDER BY score DESC) AS row
    -- 같은 순위를 허용하여 순위를 붙임
  , RANK()       OVER(ORDER BY score DESC) AS rank
    -- 같은 순위가 있을 때 같은 순위 다음에 있는 순위를 건너 뛰고 순위를 붙임
  , DENSE_RANK() OVER(ORDER BY score DESC) AS dense_rank
FROM
    popular_products
ORDER BY
    row
;
```
