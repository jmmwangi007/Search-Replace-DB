[![Build Status](https://travis-ci.org/interconnectit/Search-Replace-DB.svg?branch=4.0)](https://travis-ci.org/interconnectit/Search-Replace-DB)

# Search Replace DB - v4.0

This script was made to aid the process of migrating PHP and MySQL
based websites. Works with most common CMSes.

If you find a problem let us know in the issues area and if you can
improve the code then please fork the repository and send us a pull
request :)

## Warnings & Limitations

We can't test every possible case, though we do our best. Backups and
verifications are important.

You use this script at your own risk and we have no responsibility for
any problems it may cause.

There are many edge cases and WordPress plugins that likes to mess
your database, we don't have a silver bullet.

The license for this software is GPL v3, please bear this in mind if
contributing or branching.

*Do backups*, also *do backups* and finally *do backups*!

## Usage

1. *Do backups.*
2. Migrate all your website files.
3. Upload the script folder to your web root or higher.	
4. Browse to the script folder URL in your web browser.
5. Fill in the fields as needed.
6. Choose the `Do a safe test run` button to do a dry run without searching/replacing.

## Installation
To install the script, please place the files inside your sites public folder and head to yourWebsiteUrl/search-replace-db

### CLI script

To invoke the script, navigate in your shell to the directory to where
you installed Search Replace DB.


Type `php srdb.cli.php` to run the program. Type `php srdb.cli.php
--help` for usage information:


	-h, --host
	
		Required. The hostname of the database server.
		
	-n, --name
	
		Required. Database name.
		
	-u, --user
	
		Required. Database user.
		
	-p, --pass
	
		Database user's password.
		
	--port
	
		Optional. Port on database server to connect to.
		The default is 3306. (MySQL default port).
		
	-s, --search
	
		String to search for, `preg_replace()` style regular
		expression, or a JSON array of values to replace. 
		
	-r, --replace
	
		None empty string to replace search with,
		`preg_replace()` style replacement, or a JSON array of values to replace.
		
	-t, --tables
	
		If set only runs the script on the specified table, comma
		separate for multiple values.
		
	-w, --exclude tables
	    If set runs the script on all tables except for the specified ones, 
	    comma seperate for multiple values
	
	-i, --include-cols
	
		If set only runs the script on the specified columns, comma
		separate for multiple values.
		
	-x, --exclude-cols
	
		If set excludes the specified columns, comma separate for
		multiple values.
		
	-g, --regex [no value]
	
		Treats value for -s or --search as a regular expression and
		-r or --replace as a regular expression replacement.
		The value in -s needs to be surrounded by a delimiter such as "/" or "#" which needs to go before or after the string.
		
	-l, --pagesize
	
		How many rows to fetch at a time from a table.
		
	-z, --dry-run [no value]
	
		Prevents any updates happening so you can preview the number
		of changes to be made
		
	-e, --alter-engine
	
		Changes the database table to the specified database engine
		eg. InnoDB or MyISAM. If specified search/replace arguments
		are ignored. They will not be run simultaneously.
		
	-a, --alter-collation
	
		Changes the database table to the specified collation
		eg. utf8_unicode_ci. If specified search/replace arguments
		are ignored. They will not be run simultaneously.
		
	-v, --verbose [true|false]
	
		Defaults to true, can be set to false to run script silently.
		
	--help
	
		Displays this help message ;)

### Example cli commmands: 

```bash
php srdb.cli.php -h dbhost -n dbname -u root -p "" -s "http://www.yourdomain.com" -r "http://newdomain.com"

php srdb.cli.php -h dbhost -n dbname -u root -p "password" -s "http://www.yourdomain.com" -r "http://newdomain.com"

php srdb.cli.php -h dbhost -n dbname -u root -p "password" -s "search" -r "replace"
```

## Troubleshooting

### Nothing works after the search/replace operation!

It's time to use your backups!

### I get a popup saying there was an AJAX error

This happens occasionally and could be for a couple of reasons:

 * When the script starts, it attempts to start your WordPress or
   Drupal installation to auto-detect your username and password
   settings. If this fails, you will see a message informing you that
   auto-detection failed. You will have to enter your details
   manually.
   
 * Script was unable to set the timeout so PHP closed the connection
   before the table could be processed, this can happen on some server
   configurations.
   
## Contributing

You can view the source code and submit a pull request using GitHub,
the project's page is located at:

https://github.com/interconnectit/Search-Replace-DB/

We appreciate a small unittest among the code, please explain what
you are  is trying to solve.

# License

This file is part of Search-Replace-DB.

Search-Replace-DB is free software: you can redistribute it and/or
modify it under the terms of the GNU General Public License as
published by the Free Software Foundation, either version 3 of the
License, or any later version.

Search-Replace-DB is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with Search-Replace-DB.
If not, see <https://www.gnu.org/licenses/>.
