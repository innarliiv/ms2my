I imported an old repo from [Sourceforge](https://sourceforge.net/projects/ms2my/) to github.

I originally wrote ms2my in 2003 and I was truly surprised to get 21000+ downloads. The most unexpected and surprising fact was that it [became popular 10 years after last modification](https://sourceforge.net/projects/ms2my/files/stats/timeline?dates=2003-02-01+to+2017-09-08)!

You are all welcome to update and modernize it!

Best regards,
Innar Liiv

"ms2my" - MSSQL to MySQL converter
==================================

```
  "ms2my" is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  "ms2my" is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License
  along with "ms2my"; if not, write to the Free Software
  Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
```

  Requires:
  1) cgi-version of PHP compiled with FreeTDS (www.freetds.org)
  2) FreeTDS configured for the specific MSSQL connection

 
  0.15-beta
  Welcome to new developers James Puddicombe and Lluis Pamies!
  - slight changes in command line arguments - now possible to choose a database (instead of default)
  - better error reporting and logging of the process
  - handling zero-length column results correctly
  - handling PM times between 12:00PM and 12:59PM
  - "get only updates" feature, which is VERY experimental at the
    moment and should only be used with very special attention :-)

  0.1-alpha (by Innar Liiv)
  - Initial release
  *) as much and as few as it is needed for me to refresh mssql
     automatically to mysql every day - unfortunately no support
     for views,procedures,triggers,foreign keys etc - because
     at the moment mySQL does not support them.

INSTALLATION INSTRUCTIONS IN THE FILE CALLED "INSTALL".

README.
-------

What is ms2my all about and why was it written?
-----------------------------------------------

As everyone who has tried to establish connection to MSSQL with PHP _from *nix_ enviroment - it's
quite hard, because the standard mssql functions provided with PHP support only connection if PHP runs on Windows.

Fortunately there is a great software called FreeTDS (as said in www.freetds.org: 
FreeTDS is a set of libraries for Unix and Linux that allows your 
programs to natively talk to Microsoft SQL Server and Sybase databases).

And the programm was simply written due to a need not only once convert the information from MSSQL
(in that case it would have been a bit of hacking with export and import or some other way of "manual hacking") -
but constantly replicate the information from MSSQL to MYSQL. And because it was not a big hassle to write a
bit more universally (could have hard coded the tables and columns, u know..) - this little helping script was
born.

Simple as that - hope that does your work a bit easier next time. And if you want to contribute code also, please
write drcrm@users.sourceforge.net.

Best regards,
Innar Liiv

P.S. If ODBC (w/ or w/o FreeTDS) connection development will some day be more efective, code will probably be
rewritten - but until that - have fun :-)

BUGS
----

While reporting bugs, please keep in mind that the algorithm of dumping is running the queries:
1) DESC (tablename) (actually sp_columns (tablename) but the conversion will be done on the fly)
2) SELECT * FROM (tablename)

So - if something is not working, please show some data result examples for the previous queries also - or
it would GREAT if you could submit the patch or workaround to some project yourself and contribute it.
