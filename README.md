# Project 10 - Fortress Globitek

Time spent: **12** hours spent in total

> Objective: Create an intentionally vulnerable version of the Globitek application with a secret that can be stolen.

### Requirements

- [x] All source code and assets necessary for running app
- [x] `/globitek.sql` containing all required SQL, including the `secrets` table
- [x] GIF Walkthrough of compromise
- [x] Brief writeup about the vulnerabilities introduced below

### Vulnerabilities

Describe the vuln(s) here.

This site is vulnerable to SQL injection using the salesperson url (such as http://localhost/globitek/public/salesperson.php?id=4). Since db_escape() is not called on the url parameter, an attacker can use sqlmap in order to retrieve the contents of every table in the database, including the secrets table. By using sqlmap with the command `python2 sqlmap.py -u "http://localhost/globitek/public/salesperson.php?id=2" -D globitek -T secrets --dump` (where the '2' could be anything), we can see the values stored in the secrets table. This could be changed to any other table in the database.

GIF Walkthrough:

<img src="http://i.imgur.com/keIUTUJ.gif">
