---
layout: post
title: Using gzip and gunzip with mysql to import/export backups
---

What happens if you don’t have enough storage on your partition to have both the SQL dump and the actual data: you can import it or export it directly from the compressed file.

Exporting:

    mysqldump -u user -p database | gzip > database.sql.gz

Importing:

    gunzip < database.sql.gz | mysql -u user -p database

Another useful trick. And thanks to this, I won’t forget that syntax again. :)
