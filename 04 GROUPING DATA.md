-- GROUPING DATA WITH SQL


/*
    When we looked at aggregate functions, we applied them to entire query results.
    We could get the maximum value in a particular field across all rows, or some subset
    of the rows, if we use a where clause.

    Often what we really want to do us group our data into a number of subsets, and use the aggregate
    functions on each of those. For example, counting how many tracks use each of the 5 different Media Types.

    SQL Provides a GROUP BY feature that allows us to do this.
*/


/*
  Group By The AlbumId in the Track Table
  Show the number of rows in each group

  The results aren't very useful. We can see how many tracks are on each album,
  but not which album each result is for.
*/
**select count(*) from Track**
**group by AlbumId;**


/*
  Group By The AlbumId in the Track Table
  Show the number of rows in each group, and the AlbumId for each.

  Better, now we can see which album each row relates to. But it's still only an Id
*/
**select AlbumId, count(*) from Track**
**group by AlbumId;**


/*
  Group By The AlbumId in the Track Table
  Show the number of rows in each group, and the Album Title for each.

  Now we can see the title of the album each row relates to.
*/
**select Album.Title, count(*) from Track**
**  join Album on Track.AlbumId = Album.AlbumId**
**group by Track.AlbumId;**


/*
    The key to the group by is that the repeating value in the grouped column (AlbumId) defines a group
    of rows, that gets collapsed into one row. You can then use an Aggregate Function on that group, just as
    you previously did on entire query results.

    All of the aggregate functions work just as before.
*/

-- Find the Cheapest Track On Each Album
select AlbumId, Min(UnitPrice) from Track
group by AlbumId;


-- Find the Most Expensive Track On Each Album
select AlbumId, Max(UnitPrice) from Track
group by AlbumId;


-- Find the total cost of each album
select AlbumId, Round(Sum(UnitPrice), 2) from Track
group by AlbumId;


-- Find the total cost of each album
-- But join to the Album table to include the Title of the Album
select Album.Title, Round(Sum(UnitPrice), 2) from Track
  Inner Join Album on Track.AlbumId = Album.AlbumId
group by Track.AlbumId;


/*
    BRONZE CHALLENGES
    -----------------
 */
-- How many customers do we have in the City of Berlin
-- Expected : 2



/*
    SILVER CHALLENGES
    -----------------
    How much has been made in sales for the track "The Woman King"
    You'll need to find how many sales there are for each track in the InvoiceLine table,
    multiply by the Unit Price,
    join to the Track table to bring in the Track Name,
    and filter to find the deatils for "The Woman King"

    Expected : 3.98
*/


/*
    GOLD CHALLENGES
    -----------------
    Create a list of the top 5 acts by number of tracks.
    The table should include the name of the artist and the number of tracks they have.
    You will need to link from the Track

    Iron Maiden	    213
    U2	            135
    Led Zeppelin	  114
    Metallica	      112
    Deep Purple	    92
 */