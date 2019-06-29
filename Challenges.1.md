``` ALL TABLES ```
+-------------------+
| Tables_in_Chinook |
+-------------------+
| Album             |
| Artist            |
| Customer          |
| Employee          |
| Genre             |
| Invoice           |
| InvoiceLine       |
| MediaType         |
| Playlist          |
| PlaylistTrack     |
| Track             |
+-------------------+

mysql> desc ``` Invoice ```;
+-------------------+---------------+------+-----+---------+----------------+
| Field             | Type          | Null | Key | Default | Extra          |
+-------------------+---------------+------+-----+---------+----------------+
| InvoiceId         | int(11)       | NO   | PRI | NULL    | auto_increment |
| CustomerId        | int(11)       | NO   | MUL | NULL    |                |
| InvoiceDate       | datetime      | NO   |     | NULL    |                |
| BillingAddress    | varchar(70)   | YES  |     | NULL    |                |
| BillingCity       | varchar(40)   | YES  |     | NULL    |                |
| BillingState      | varchar(40)   | YES  |     | NULL    |                |
| BillingCountry    | varchar(40)   | YES  |     | NULL    |                |
| BillingPostalCode | varchar(10)   | YES  |     | NULL    |                |
| Total             | decimal(10,2) | NO   |     | NULL    |                |
+-------------------+---------------+------+-----+---------+----------------+

mysql> desc ``` Customer ```;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| CustomerId   | int(11)     | NO   | PRI | NULL    | auto_increment |
| FirstName    | varchar(40) | NO   |     | NULL    |                |
| LastName     | varchar(20) | NO   |     | NULL    |                |
| Company      | varchar(80) | YES  |     | NULL    |                |
| Address      | varchar(70) | YES  |     | NULL    |                |
| City         | varchar(40) | YES  |     | NULL    |                |
| State        | varchar(40) | YES  |     | NULL    |                |
| Country      | varchar(40) | YES  |     | NULL    |                |
| PostalCode   | varchar(10) | YES  |     | NULL    |                |
| Phone        | varchar(24) | YES  |     | NULL    |                |
| Fax          | varchar(24) | YES  |     | NULL    |                |
| Email        | varchar(60) | NO   |     | NULL    |                |
| SupportRepId | int(11)     | YES  | MUL | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+