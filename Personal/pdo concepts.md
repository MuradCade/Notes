# Learning pdo concept with php

what is pdo?

PDO in PHP (PHP Data Objects) is **a lightweight, consistent framework for accessing databases in PHP**

we will create simple crud webapplication using pdo

## Table of content

1. connect to database usin pdo

2. insert data to database using pdo

3. display all data / filtering using pdo

4. update data inside database using pdo

5. delete data using pdo

## 1- Connection to database

code below shows how to connect to database using pdo.

```php
$servername = 'localhost';
$username = 'root';
$pwd = '';
$dbname='pdo';

try {

$conn = new PDO('mysql:host'.$servername.';dbname'.$dbname.';charset=utf8',$username,$pwd);
echo 'success'; // display success message
} catch (\Throwable $th) {
    //display message error
   echo $th->getmessage();
}
```

## 2- insert data into database
