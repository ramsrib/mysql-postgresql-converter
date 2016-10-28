MySQL to PostgreSQL Converter
=============================

Lanyrd's MySQL to PostgreSQL conversion script.

This script was designed for our specific database and column requirements - notably, it places indexes on all foreign keys and maintains the same size of varchar.

How to use
----------

First, dump your MySQL database in PostgreSQL-compatible format


With data:

    `mysqldump --compatible=postgresql --default-character-set=utf8 -r scrumworks.mysql -u root scrumworks`

or

Without data:

  `mysqldump --compatible=postgresql --default-character-set=utf8 --no-data --skip-add-drop-table -r scrumworks.mysql -u root -p scrumworks`


Then, convert it using the dbconverter.py script:

`python db_converter.py scrumworks.mysql scrumworks.psql`

It'll print progress to the terminal.

Finally, load your new dump into a fresh PostgreSQL database using:

`createdb cake`

`psql cake < scrumworks.psql`


Note:
  - It doesn't create sequences and full-text keys.

More information
----------------

You can learn more about the move which this powered at http://lanyrd.com/blog/2012/lanyrds-big-move/ and some technical details of it at http://www.aeracode.org/2012/11/13/one-change-not-enough/.
