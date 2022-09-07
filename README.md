


<h1 style="font-size:50px"><img src="https://carfest.ge/images/landing/r6.png" width="200" />Carfest</h1>

Carfest - is a web application, created for our startup with the same name. This website contains information about Carfest services and all the available cars. It contains useful features like a leasing calculator, damage assessment, and many others.  Carfest makes the process of getting a new car a simple and comfortable experience.

## Table of Contents 

* [Prerequisites](#prerequisites)
* [Tech Stack](#tech-stack)
* [Getting Started](#getting-started)

#
<h2 id="prerequisites">Prerequisites:</h2>

<table>
    <tr>
        <td>✔️ </td>
        <td><img src="https://w7.pngwing.com/pngs/751/3/png-transparent-logo-php-html-others-text-trademark-logo-thumbnail.png" width="35" style="position: relative; top: 4px" /></td>
        <td>PHP@8.x</td>
    </tr>
    <tr>
        <td>✔️ </td>
        <td><img src="readme/assets/mysql.png" width="35" style="position: relative; top: 4px" /></td>
        <td>MySQL@8 and up</td>
    </tr>
    <tr>
        <td>✔️</td>
        <td><img src="readme/assets/npm.png" width="35" style="position: relative; top: 4px" /></td>
        <td>npm@6 and up</td>
    </tr>
    <tr>
        <td>✔️ </td>
        <td><img src="readme/assets/composer.svg" width="35" height="30" style="position: relative; top: 5px" /></td>
        <td>composer@2 and up</td>
    </tr>
    <tr>
        <td>✔️ </td>
        <td><img src="readme/assets/redis.png" width="55" height="35" style="position: relative; top: 5px" /></td>
        <td>Redis Server @5.0.7 and up</td>
    </tr>
</table>


#
<h2 id="tech-stack">Tech Stack:</h2>

<table>
    <tr>
        <td>✔️</td>
        <td><img src="readme/assets/laravel.jpg"  height="18" style="position: relative; top: 4px" /></td>
        <td><a href="https://laravel.com/docs/6.x" >Laravel@8.x</a></td>
        <td>-</td>
        <td>Back-End framework</td>
    </tr>
    <tr>
        <td>✔️</td>
        <td><img src="readme/assets/nova.png"  height="17" style="position: relative; top: 4px" /></td>
        <td><a href="https://nova.laravel.com/" >Laravel Nova</a></td>
        <td>-</td>
        <td>flexible Admin Panel as carfest "Super Admin"</td>
    </tr>
    <tr>
        <td>✔️</td>
        <td><img src="readme/assets/laravelMix.png" height="18" style="position: relative; top: 4px" /></td>
        <td><a href="https://laravel-mix.com/" >Laravel Mix</a></td>
        <td>-</td>
        <td>is a webpack wrapper which makes an ease for a developer to start working on JS files and compile them with such simplicity</td>
    </tr>
    <tr>
        <td>✔️</td>
        <td><img src="readme/assets/translation.jpg" height="19" style="position: relative;   top: 4px" /></td>
        <td><a href="https://github.com/barryvdh/laravel-translation-manager" >Laravel    Translation Manager</a></td>
        <td>-</td>
        <td>package for translation</td>
    </tr>
</table>


#
<h2 id="getting-started">Getting Started</h2>

* [Pull from the Git Repository](#git)
* [Configure .env File](#env)
* [Create Database](#database)
* [Install Redis Server](#redis-server)
* [Synch Database](#synch-db)
* [Synch Storage](#synch-storage)
  

<h3 id="git">🚗 Pull Git Repository & install Dependencies</h3>


1\. Clone Carfest repository from github:
```sh
git clone https://github.com/RedberryProducts/carfest
```

2\. Install PHP dependencies:
```sh
composer install
```

3\. Install JavaScript dependencies:
```sh
npm install
```

4\. Build your JS/SaaS resources:
```sh
npm run dev
```
<h3 id="env">🚗 Configure .env File:</h3>

1\. First Create **.env** file on base of **.env.example** in the **root of your project**:

```sh
cd [PROJECT_ROOT]
cp .env.example .env
```
2\. Provide **.env** file for all the necessary environment variables:


#
**Laravel Nova:**
add nova_guard at the bottom:
>NOVA_GUARD=admin

#
**MySQL:**
>DB_CONNECTION=mysql <br />
>DB_HOST=127.0.0.1 <br />
>DB_PORT=3306 <br />
>DB_DATABASE=***** <br />
>DB_USERNAME=***** <br />
>DB_PASSWORD=***** <br />

>⚠️ if you're not planning to conenct to existing DataBase, You'll have to configure DB-Credentials after you create your own Database. 


#
**OLeasing:**
>LEASING_HOST=https://oleasing.ge <br />
>LEASING_USER=***** <br />
>LEASING_PASSWORD=***** <br />



#
3\. After setting up **.env** file, cache environment variables:
```sh
php artisan config:cache
```

4\. Execute this command in the root of you project, to generate auth key:
```sh
  php artisan key:generate
```

5\. Execute this command in the root of you project, to Link the Storage:
```sh
  php artisan storage:link
```


5\. Also execute following command to cache importData.xlsx file thats used by import calculator:
```sh
  php artisan cache:importData
```
#

<h3 id="database">🚗 Create Database</h3>

in case you don't want to connect to existing database and you want to create your own local database execute following instructons:

1\. open your terminal and access MySQL:

```sh
sudo mysql –u root –p
```


2\. Create a new MySQL user (if you don't already have one):

```sql
CREATE USER 'database_user'@'localhost' IDENTIFIED BY 'password';
```


3\. Create DataBase:

```sql
CREATE DATABASE db_name;
```


4\. Grant All Previlegies to your User:

```sql
GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';
```

5\. Update Configuration (.env file)  in your project:

>DB_DATABASE=database_name <br />
>DB_USERNAME=database_user <br />
>DB_PASSWORD=password <br />

6\. Run Migrations:

```php
php artisan migrate
```

7\. Seed the DataBase:

```php
php artisan db:seed
```


<h3 id="redis-server">🚗 Install Redis Server</h3>

Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker. Redis provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams. For more info click [here](https://redis.io/).

1\. To install Redis-Server run:
```sh
sudo apt-get install redis-server
redis-server
```

2\. To run redis-server execute:
(when you work on your project redis-server must be runing)
```sh
redis-server
```

<hr />

<h3 id="synch-db">🚗 Synchronize Database</h3>

After Creating the DataBase take BackUp from test server and update your Data.

>❗❗❗ currently testing and production versions are published both on the same server.
all the instructions are ment to be done on testing version. both storage and database.
we're planing to move testing environment to an independent server in the future. 

>⚠️  please don't mess around with production version.
That way you might awaken the sleeping dragon. 🐉🔥

1\. access server from your terminal
```sh
ssh forge@carfest.ge
```

2\. Navigate to the testing environment.
```sh
cd test.carfest.ge/current
```

3\. dump the Database.
```sh
mysqldump -uroot -p database_name > dumpfilename.sql
```

4\. Move generated dump file to the public folder

5\. Download it to your Device

6\. On your Device navigate and move your dump file to the Root directory of your project.

7\. Update your database with the BackUp you took from the server.
```sh
mysql -uroot -p database_name < dumpfilename.sql
```

<h3 id="synch-storage">🚗 Synchronize Storage</h3>

It's also important that you update storage in your project so images will be synched

1\. access server from your terminal
```sh
ssh forge@carfest.ge
```

2\. go to the storage and navigate to the storage/app folder
```sh
cd test.carfest.ge/current/storage/app
```

3\. Zip the public folder.
```
zip -r zipperPictures.zip public
```

4\. Move generated zip file to the public folder

5\. Download it to your Device
```sh
simply visit the following url: test.carfest.ge/zipperPictures.zip
```

6\. On your Device navigate to the Root directory of your project, then navigate to storage/app.

7\. delete your public folder in storage/app directory.

8\. unzip your zip file:
```
unzip zipperPictures.zip
```