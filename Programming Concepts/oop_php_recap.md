Object Oriented Programming continue 

## 1- Triats

Traits are used when you need to extend more then one class.

triat are use in sensitive situation just imagine you have 3 class , first one is called database and it contains connection of database , the second one is called role it has all methods needed to verify user role and the last you have delete user class.

in the scenario we need to delete. you can use trait when extend is not avaliable.

### Traits Code

```php
<?php

class database {
    // contains method that responsible to connect to database
    public function connectodb(){
    return 'database connected successfully;';
}

}
trait  userRole{
    // below method check if userrole is admin or not

    public function roles($role){
    if($role == 'admin'){
    return true;
}else{
    return false;
}

}

}

class deleteuser extends database{

    //intiate triat
    use userRole;
    // check if database connection success
    public function checkdb(){
    return $this->connectodb();
}

// check if the user is admin or normal user to delete user in db
public function delete($role){
    if($this->roles($role)){
    echo 'user deleted successfully ';

}else {
    echo 'only admin are allowed to delete users';
}

}

}
// create instance of deleteuser class
$object = new deleteuser();


//delet user method
echo $object->delete('admin');

//output : if delete pramater is admin : user deleted successfully,
// if not ouput: only admin are allowed to delete users
```

## 2- Abstract

abstract is term that enables you to over ride the existing method , in abstract methods only have name they have body,abstract uses extend when following its role.

### Abstract Code

```php
<?php

// absctract class always start with abstract
abstract class Studentinfo{
    //method below is responsible to add new student information
    abstract function addstudentinfo();

    // method below is responsible to display student information
    abstract function getstudentinfo();
}



//in order to use abstract class and its function i have to create new class

class studentoperations extends Studentinfo{
    public function addstudentinfo(){
        return 'student added successfully<br>';

    }

    public function getstudentinfo(){
        return 'all students data are been displayed';
    }
}

// create instance of class studentoperation which follows the rules of abstract class named studentinformation
$object = new studentoperations();
echo $object->addstudentinfo();
echo $object->getstudentinfo();

//output : student added successfully, all students data are been displayed
```

```.htaccess
RewriteEngine On
RewriteBase /<app>/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . index.php [L]
```
