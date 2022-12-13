
## 각 카테고리의 상위 n개 추출하기

```sql
-- # 각 카테고리의 상위 n개 추출하기
SELECT *
FROM
	-- 서브 쿼리 내부에서 순위 계산하기
    ( SELECT
     	  category
     	, product_id
     	, score
     	  -- 카테고리별로 점수 순서로 유일한 순위를 붙임
     	, ROW_NUMBER()
     		OVER(PARTITION BY category ORDER BY score DESC)
     	  AS rank
       FROM popular_products
     ) AS popular_products_with_ranks
-- 외부 쿼리에서 순위 활용해 압축하기
WHERE rank <= 3
ORDER BY category, rank
;
```

## 각 카테고리에서 최상위 상품 추출하기

```sql
-- # 각 카테고리에서 최상위 상품 추출하기
-- DISTINCT 구문을 사용해 중복 제거하기
SELECT DISTINCT
	  category
      -- 카테고리별로 순위 최상위 상품 ID 추출하기
    , FIRST_VALUE(product_id)
      OVER(PARTITION BY category ORDER BY score DESC
           ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING)
      AS product_id
FROM popular_products
;
```