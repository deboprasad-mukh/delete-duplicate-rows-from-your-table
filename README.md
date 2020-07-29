# delete-duplicate-rows-from-your-table
*\\This will delete duplicate rows, except the first row
*\\ I am using oracle SQL developer 

query1.1 : DELETE FROM table_name
WHERE
    RowID NOT IN ( 
SELECT MIN(RowID) FROM table_name
        GROUP BY
 Column1, Column2, Column3   
)
[[[[[ this will compare your rows to each row numbers and if there is slight changes there it will treat it as a different or unique column]]]]]
example : 
ACCOUNT_NUMBER	        CARD_NUMBER	     CARD_TYPE
09241A1272	         0123-4567-0924-1272	DEBIT
09241A1273	         0123-4567-0924-1273	DEBIT
09241A1274	         0123-4567-0924-1274	ATM
09241A1274	         0123-4567-0924-1274	null
09241A1274	         0123-4567-0924-1274	ATM

by using query 1.1 we will get :  1 rows deleted (last row)
if we want to delete it by grouping single column then the code is
query1.2: DELETE FROM cardinfo
WHERE
    RowID NOT IN (
        SELECT MIN(RowID) FROM cardinfo
        GROUP BY ac_num 
         
    )

*\\then it will delete last two rows
