Phing based migrator
====================

Requirements
============

Php 5.3 + php5-curl extension installed. Check curl install: `php -i|grep -i curl`

Install
=======

1. Download composer manually to current directory or run `php -r eval('?>'.file_get_contents('https://getcomposer.org/installer'));`
2. Install phing `php composer.phar install`
3. Setup database in config/parameters/loc.properties or create custom settings file and replace and set proper value db.parameters.file in config/parameters/build.properties
4. Check available tasks: `php vendor/bin/phing -l`

Use
===

1. Create migration template: `php vendor/bin/phing migration.create` and edit migrations/deltas/<timestamp>-dbdeploy.sql
2. Apply migration: `php vendor/bin/phing migration.up`
3. You can add db-patches as simple sql dumps to migrations/patches/${dev}/*.sql, that will always be executed after each migration.up task
4. You can specify ${dev} variable environment, ex: `php vendor/bin/phing migration.create -Ddev=prod`
5. You can redifine db-settings file with `php vendor/bin/phing migration.create -Ddb.file=config/parameters/my_db.properties`

Links
=====

Check dbdeploy task for migration format http://www.phing.info/docs/guide/stable/chapters/appendixes/AppendixC-OptionalTasks.html
