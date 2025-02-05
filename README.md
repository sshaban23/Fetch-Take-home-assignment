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




