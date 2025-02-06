# Fetch-Take-home-assignment

**Question 1: "Are there any data quality issues present?"**

Answer: 

Yes. In the USER file, there are columns like name, state, birth date etc. all have some missing rows/values, and the gender column has many inconsistent responses like "My gender isn't listed" or "non_binary" or "Non-Binary" which have to be cleaned up.

In the TRANSACTIONS file, the "BARCODE" column has missing rows and inconsistent numbers for the barcodes.

Also, 
In the PRODUCTS file, the column names CATEGORY_1	to CATEGORY_4 are ambigious. 
MANUFACTURER has rows called "PLACEHOLDER MANUFACTURER" which could cause issues in the future. BRAND also has alot of missing rows.



**Question 2: "Are there any fields that are challenging to understand?"**

Answer:

Yes, all the CATEGORY columns in the PRODUCTS table are not clear, and does not show how they are related to each other or if they are necessary for analysis. 

In USER table, the column "LANGUAGE" has rows that are "en" or "es-419" which doesn't make sense and would need more clearification.

Also, "SCAN_DATE" field and "PURCHASE_DATE" field in the TRANSACTION table are confusing since some of them are on the same date but others are inconsistent.


**Question 3: What are the top 5 brands by receipts scanned among users 21 and over?**

**SQL CODE:**

SELECT p.BRAND, COUNT(*) AS total_receipts

FROM TRANSACTIONS t

JOIN USERS u ON t.user_id = u.ID

JOIN PRODUCTS p ON t.BARCODE = p.BARCODE

WHERE (strftime('%Y', 'now') - strftime('%Y', u.BIRTH_DATE)) >= 21

GROUP BY p.brand

ORDER BY total_receipts DESC

LIMIT 5;


Answer: 
1 - COCA-COLA
2 - ANNIE'S HOMEGROWN GROCERY
3 - DOVE
4 - BAREFOOT
5 - ORIBE


**QUESTION 4: What are the top 5 brands by sales among users that have had their account for at least six months?**

**SQL CODE**

SELECT p.brand, SUM(t.FINAL_SALE) AS total_sales

FROM TRANSACTIONS t

JOIN USERS u ON t.user_id = u.ID

JOIN PRODUCTS p ON t.BARCODE = p.BARCODE

WHERE (strftime('%Y', 'now') - strftime('%Y', u.CREATED_DATE)) * 12 +

      (strftime('%m', 'now') - strftime('%m', u.CREATED_DATE)) >= 6
      
GROUP BY p.brand

ORDER BY total_sales DESC

LIMIT 5;

Answer: 

1 - COCA-COLA -- 2592.1
2 - ANNIE'S HOMEGROWN GROCERY -- 2383.92
3 - DOVE -- 2327.47
4 - BAREFOOT -- 2284.59
5 - ORIBE -- 2085.93



**QUESTION 5: Who are Fetch’s power users?** 

**SQL CODE**

