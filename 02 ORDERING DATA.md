-- ORDERING DATA WITH SQL


-- Select all columns from the Album table
-- Sort the results by title
select * from Album
order by Title;


-- Select all columns from the Album table
-- Sort the results by title descending
select * from Album
order by Title desc;


-- Select all columns from the Album table
-- Sort by ArtistId, and within that by Title
select * from Album
order by ArtistId, Title;


-- Select all columns from the Album table
-- Sort by ArtistId Ascending, and within that by Title Descending
select * from Album
order by ArtistId, Title Desc;


-- Join the Track and Album tables to show track names and album titles.
-- Sort by Album title, then by Track Name
select Track.Name, Album.Title from Track
join Album on Track.AlbumId = Album.AlbumId
order by Album.Title, Track.Name;


/*
  Select the Invoice Date, BillingCite and Total from the Invoice table
  Sort by Total, descending. And limit to the top 5 results

  Expected :
    2013-11-13 00:00:00	  Prague	      25.86
    2012-08-05 00:00:00	  Fort Worth	  23.86
    2010-02-18 00:00:00	  Budapest	    21.86
    2011-04-28 00:00:00	  Dublin	      21.86
    2010-01-18 00:00:00	  Vienne	      18.86
*/

select InvoiceDate, BillingCity, Total from Invoice
order by Total desc
limit 5;



/*
    CHALLENGES
    ----------

    Complete the following exercises, the expected results are shown, you need to write the queries.
*/

/*
  BRONZE CHALLENGES
  -----------------

  1. Select the InvoiceDate, BillingAddress, and Total from the Invoices table,
     Ordered by InvoiceDate Descending

     Expected : 412 rows (starting with the following)
     2013-12-22 00:00:00	  12,Community Centre	                        1.99
     2013-12-14 00:00:00	  Porthaninkatu 9	                            13.86
     2013-12-09 00:00:00	  Rua dos Campeões Europeus de Viena, 4350	  8.91
*/
select InvoiceDate, BillingAddress,Total 
from Invoice 
order by InvoiceDate desc;

/*
  2. We need to fire the last three people hired.
     Select the EmployeeId, LastName, FirstName and HireDate
     of the 3 Employees with the most recent HireDate

     Expected : 3 rows (starting with the following)
      8	  Laura	  Callahan	  2004-03-04 00:00:00
      7	  Robert	King	      2004-01-02 00:00:00
      5	  Steve	  Johnson	    2003-10-17 00:00:00
*/
select EmployeeId, LastName, FirstName, HireDate 
from Employee 
order by HireDate 
limit 3;


/*
  SILVER CHALLENGES
  -----------------

  3. Disaster, we've heard from Steve Johnson's lawyers.
     He claims that Michael Mitchell was hired on the same day as him,
     but was hired later in the day. Mitchell should have been let go, not him.

     Confirm this by extending the number of results and make sure nobody else was
     hired on that day.

     Then modify the query to return the correct 3 people.

     Continue to use HireDate as the primary sort column, but use EmployeeId as the tie breaker.
     Assume that a higher EmployeeId means they were hired later.

     Expected : 3 rows (starting with the following)
      8	  Laura	  Callahan	  2004-03-04 00:00:00
      7	  Robert	King	      2004-01-02 00:00:00
      6	  Michael	Mitchell	  2003-10-17 00:00:00
*/
mysql> select EmployeeId, FirstName, LastName, HireDate 
from Employee 
order by HireDate desc,EmployeeId desc ;




/*
  GOLD CHALLENGES
  -----------------

  4. Create a query that shows our 10 biggest invoices by Total value, in descending order.
     If two invoices have the same Total, the more recent should appear first.
     The query should also show the Name of the Customer

     An Easy way to show the name would be to include the FirstName and LastName columns from
     the Customer table. However, if you use the concatenation operator you can combine those
     fields into one column in the results.

     Expected: 10 rows

      Helena Holý	            2013-11-13 00:00:00	  25.86
      Richard Cunningham	    2012-08-05 00:00:00	  23.86
      Hugh O'Reilly	          2011-04-28 00:00:00	  21.86
      Ladislav Kovács	        2010-02-18 00:00:00	  21.86
      Victor Stevens	        2011-05-29 00:00:00	  18.86
      Astrid Gruber	          2010-01-18 00:00:00	  18.86
      Luis Rojas	            2010-01-13 00:00:00	  17.91
      Isabelle Mercier	      2012-10-06 00:00:00	  16.86
      František Wichterlová	  2012-09-05 00:00:00	  16.86
      Bjørn Hansen	          2011-06-29 00:00:00	  15.86
*/
Invoices by Total order by limit 10

select concat(FirstName," ", LastName), InvoiceDate, Total
from Customer
join Invoice on Customer.CustomerId = Invoice.CustomerId
order by Total desc, InvoiceDate desc
limit 10;