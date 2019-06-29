-- INSERTING DATA WITH SQL


/*
  So far we've focused on the SQL 'SELECT' command that lets us get data out of our database.
  Variations of the SELECT command allow us to filte, order, and aggregate the data.

  Now, we're going to look at the SQL 'INSERT' command, which, as you might have guessed, allows us
  add new data to the database.
*/


/*
  An Insert statement consists of the table we want to insert into,
  the columns with than table that we want to set values for,
  and the values for those columns.

  Let's start by inserting a new media type.
  We insert into the MediaType table.
  We insert into just the 'Name' column, the id will be generated automatically.
  We specify a value of "Test Media Type 1" for the name of the media type.
  If you run this statement multiple times,
  you'll get multiple new rows, with the same Name,
  but different MediaTypeIds
 */
**insert into MediaType (Name) values ("Test Media Type 1");**



/*
  Artist 150 is U2. If you look in the Album Table you'll see some Albums are missing.
  Let's insert the Album "Boy".
  To do this we need to insert both the Title of the Album ("Boy"), and the ArtistId (150)
*/
insert into Album (Title, ArtistId)
  values ("Boy", 150);


/*
  Inserting a row in the Album table is fine, but the album won't have any tracks unless we insert into the
  Track table. The Track table has quite a few more columns than album, so we have more data to insert.
  You can see the track listing here: https://en.wikipedia.org/wiki/Boy_(album)#Track_listing
*/

insert into Track (Name, AlbumId, MediaTypeId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
  values(
    -- insert list of values here
  );

/*
  So, where to the list of Values come from?

  The Name of the track can be gotten from the Track Listing.
  Set the Composer to 'U2'.
  You can also get Milliseconds from the Track Listing above.
  Set Bytes to 1234 for all tracks. This isn't strictly speaking correct, but will suffice.
  Set UnitPrice to 0.99
  That leaves AlbumId, MediaTypeId, and GenreId. All of these are foreign keys to other tables.
  You'll need to look in those tables to get the values we want to insert.
  You need to find:
    The AlbumId of the Album "Boy"
    The MediaTypeId of the MediaType "Prodected AAC audio file"
    The GenreId of the Genre "Rock"
  We could have used any MediaType and Genre, but the Album has to be the "Boy" album we created above.
  Below I have listed an example of the insert statement. Make sure you actually use the ID's
 */

-- Get the MediaTypeId
-- Expected : 348
select AlbumId from Album where Title = "Boy";

-- Get the MediaTypeId
-- Expected : 2
select MediaTypeId from MediaType where Name = "Protected AAC audio file";

-- Get the GenreId
-- Expected : 1
select GenreId from Genre where Name = "Rock";

-- Insert a Track
insert into Track (Name, AlbumId, MediaTypeId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
  values("I Will Follow", 348, 2, 1, "U2", 220000, 1234, 0.99);


/*
  BRONZE CHALLENGES
  -----------------
  Insert the remaining Tracks for the Album Boy (except for the last 2-3, insert those as part of Gold)
 */


/*
  SILVER CHALLENGES
  -----------------

  Run the following Query.
  It gives an error. Read and understand the error, then fix the problem.

  Insert into Track (Name, AlbumId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
  values("Extra Track", 348, 1, "U2", 290000, 1234, 0.99);
*/


/*
  GOLD CHALLENGES
  -----------------
  Use 1 insert statement to insert multiple tracks at the same time.
  Use Google to find the correct syntax for the Insert statement to do this.
*/