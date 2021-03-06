Postgre SQL navodila
====================
====================

Splošni ukazi v command line
############################

\c <database_name>
\connect <database_name>


SQL ukazi
############################
https://www.postgresql.org/docs/9.6/static/sql-commands.html



Izdelava uporabnika
*******************

# create role
# možnosti : https://w3resource.com/PostgreSQL/postgresql-database-roles.php



Izdelamo uporabnika
-------------------

.. code-block:: none

    sudo postgres
    psql
    CREATE ROLE <username> WITH SUPERUSER LOGIN CREATEDB CREATEROLE PASSWORD '<password>'

.. glossary::

    username
        uporabniško ime novega uporabnika

    password
        geslo, ki jo dodelimo novemu uporabniku



Superuser pravice na voljo uporabniku
-------------------------------------

.. glossary::

    LOGIN
        lahko se logira v bazo

    CREATEDB
        lahko izdela novo bazo
    
    CREATEROLE
        lahko dodaja nove uporabnike



Pregled uporabnikov
-------------------

.. code-block:: python

    \du # seznam uporabnikov
    q # greš ven iz ukaznega polja




PSQL backup --> S3
##################

Viri
****

* https://zaiste.net/posts/backup_postgresql_to_amazon_s3/
* http://docs.aws.amazon.com/cli/latest/index.html
* https://www.postgresql.org/docs/9.6/static/app-pgdump.html
* https://www.postgresql.org/docs/9.6/static/app-pgrestore.html
* http://crontab.org/
* http://www.adminschoice.com/crontab-quick-reference
* https://crontab.guru/
* https://help.ubuntu.com/lts/serverguide/backup-shellscripts.html
* https://help.ubuntu.com/community/CronHowto
* http://www.lifelinux.com/how-to-startstoprestart-cron-service-in-linux/


Uporabljeni programi
********************

pg_dumb – izdelava backup postgresql baz
pg_restore – restore backupa
aws cli – pošiljanje datotek na aws s3

Instalacija
***********
-	pip install awscli
-	pg_dumb, pg_restore pride že z postgreSQL



Izdelava BACKUP
***************

pg_dump -Fc mydb > db.dump

Komanda od majstru:
PGPASSWORD=YOUR_PASSWORD pg_dump -Fc --no-acl -h localhost -U YOUR_USER YOUR_DB > backup.dump


RESTORE BACKUP

pg_restore -c -C -d postgres db.dump
-	(-c) drop database (clean setup)
-	(-C) create database
-	(-d) log in to database and restore dumb
-	(postgres) user
-	(db.dumb) dumb file



POŠLJI NA AMAZON S3
*******************

Inštalacija
Sudo apt-get install awscli
aws s3 mv test.txt s3://mybucket/test2.txt



Kopiranje iz ali v s3
*********************

aws s3 cp <path from> <path to>
path from ali <path to> = s3://<mybucket>/<file name>.xxx
