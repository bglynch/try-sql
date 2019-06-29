-- AGGREGATING DATA WITH SQL

-- Aggregate functions allow us to calculate some value from data.

/*
    Count how many rows are in the Customer Table
    Expected : 59
 */
**select count(*) from Customer;**

/*
    What Happens if we replace the wildcard '*' with a column?
    The answer is still 59. The count() function counts how many 'rows' are in the query results.
    The '*' or column name(s) only affects how many columns there are.
    Expected : 59
 */
**select count(FirstName) from Customer;**


/*
    What can you do to change the number of 'rows' in the results, so that count returns a different value?
    How about filtering, with a Where clause?
    If we count the number of customers called Frank, we find there are only 2
    Expected : 2
 */
**select count(*) from Customer**
**where FirstName = "Frank";**


/*
    The count function is concerned only with the number of rows in a query result. It says nothing about the
    actual data values. But there are other aggregate functions. Like the following:
 */


-- Expected : Almeida
**select min(LastName) from Customer;**


-- Expected : Zimmermann
**select max(LastName) from Customer;**


-- Expected : 5.651941747572825
**select avg(Total) from Invoice;**


-- Expected : 5.65
**select round(avg(Total),2) from Invoice;**


/*
  Aggregate Functions can sometimes allow us to verify the same information from two sources.
  Here is the Total value for Invoice 2

  Expected : 3.96
*/
**select total from Invoice where InvoiceId = 2;**


/*
  Here's what we get by taking the line items from that invoice, multiplying the Price by Quantity,
  to get the total for each line item. Then using the sum function to get the total for the the invoice.

  Expected : 3.96
*/
**select sum(UnitPrice * Quantity) from InvoiceLine**
**where InvoiceId = 2;**



/*
    BRONZE CHALLENGES
    -----------------
 */
-- **On what date was our most recent employee hired?**
-- Expected : 2002-04-01 00:00:00
```  ```

-- **What is the date of mirth of our youngest employee?**
-- Expected : 1973-08-29 00:00:00
```  ```


-- **How Many Customers is Employee 4 the Sales Support Agent For?**
-- Expected : 20
```  ```


/*
    SILVER CHALLENGES
    -----------------
    **How Many Customers is Jane Peacock the Sales Support Agent For?**
    **You'll need to join the Employee and Customer Tables for this one.**

    Expected : 21
    
    ```  ```
*/



/*
    GOLD CHALLENGES
    -----------------

    Which Media Type is most popular?
    How could you answer this with a single query?
    You probably can't based on what you know so far. We'll get there.
    For now, you can use a separate query for each media type so see how many tracks use it.

    Expected : MPEG audio file
*/