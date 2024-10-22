today we will learn object oriented concept specifically in PHP.
in order to understand object oriented we will discuss the following concepts:-
- [ ] Class and Objects ,
- [ ] Method (function) and Properties (variables)
- [ ] Access Modifiers in Properties and Methods
- [ ] Magic functions such as Construct and Destruct
- [ ] Inheritance
- [ ] Getters and Setters
- [ ] Type Decoration / Type Hinting





## 1- Class and Objects Explained
what is a class and object?
class is blue print/skeleton that contains properties and methods.
object is instance of class, in order to use class you should make instance of it.
class code :-
```php
//below is class named book and its empty class
class books{
	
}

//below is an object , its instance of class
$object = new books();
```
	
## 2- Methods and Properties Explained
what is Method and Property?
method is function but its inside of class, its has the same functionality as function.
property is variable but its inside the class, it has the same functionality as variables.
code below:-
```php
//class with property and methods
class books{
	//property named bookname
	public $bookname = 'php 1st edition';
	//method named getbook that returns value of property bookame
	function getbook(){
		return $this->bookname;
	}
}

// create instance/object of class
$object = new books();
// you can't access property outside of the class without using access modifier , that way u see property bookname has public modifier.
echo $object->$bookname;
// called the method named getbook directly to display value of the property
echo $object->getbook();

//output : php 1st edition , php 1st edition
```

- code above shows us that we can access property value directly outside class or we can use method to return the value of property

## 3- Access Modifiers in Properties and Methods Explained
what is access modifiers?
access modifiers control the extent of accessibility or visibility of the class properties and methods, there are 4 access modifiers in PHP:-
- [ ] Public 
- [ ] Private
- [ ] Static
- [ ] Protected

 ### i- Public Modifier
 this modifier is public , any method or property with public modifier can be access it outside the class, code below below demonstrate it.
```php
  //class with property and methods
class books{
	//property named bookname
	public $bookname = 'php 1st edition';
	//method named getbook that returns value of property bookame
	
}

// create instance/object of class
$object = new books();
// display value of property bookname
echo $object->bookname;

//output : php 1st edition
  
```

### ii- Private Modifiers
this modifier is private, any method or property can't be accessed outside of class, only way to access it can be returning another method data to another method or using method to access property,
- [ ] example below shows how to access private property.
```php
class books{
	// below is private property with value
	private $bookname = 'php 1st edition';

	// in order to access private property data we should use method with public name
	public function getbookname(){
			return $this->bookname;
	}
}

// create instance of class books
$object = new books();
//don't say this $object->bookname;  it won't work.
// display the value of the bookname property using getbookname method
echo $object->getbookname();
//output : php 1st edition
```
- [ ] example below shows to access private methods
```php
class books{
	//private property
	private $bookname;
	// private method
	private function setbookname(){
		return $this->bookname = 'php 1st edition';
	}
	// get the return value from private method and storing it inside public function called displaybookname
	public function displaybookname(){
		return $this->setbookname();
	}
}
//create instance of class
$object = new books();
// display value of bookname from public method displaybookname
echo $object->displaybookname();
// output : php 1st edition
```


### iii- Static Modifier
This modifier is static, is used to declare properties and methods of a class as static. Static properties and methods can be used without creating an instance of the class. The static keyword is also used to declare variables in a function which keep their value after the function has ended.

- [ ] Static Modifier with property
```php
class books{
	static $bookname = 'php 1st edition';
	
	
}
// display value of static property called bookname
echo books::$bookname;
// or you can display it like mention below
$object = new books();
// display value of static property called bookname
echo $object::$bookname;

//output : php 1st edition
```

- [ ] Static Modifier with methods
```php
class books{
	static $bookname = 'php 1st edition';
	static function getbookname(){
	return self::$bookname;
	}
	
	
}
echo books::getbookname();
// or you can display it like mention below
$object = new books();
// display value of static property called bookname
echo $object::getbookname();
```

### iv- Protected Modifier
what is protected modifier?
protected modifier works on inheritance and it protect methods and properties access in it out side class , you need 2 classes to display properties and methods  data.

- [ ] Protected modifier in property
```php
// code below we have 2 classes , first class is called books the second class is called author , we will pass bookname property value inside books class to author class using inheritance
class books{
	protected $bookname = 'php 1st edition';

}

class author extends books{
	// method you can make it public or leave it without modifier and it won't make any difference.
	 public function getbookname(){
		return $this->bookname;
	}
}

$object = new author();
echo $object->getbookname();
//output : php 1st edition
```

- [ ] Protected modifier in method
```php
// code below we have 2 classes , first class is called books the second class is called author , we will pass method value  inside books class to author class using inheritance
class books{
	// empty protected bookname property
	protected $bookname;
	// assign value to bookname property within inside the function called setbookname
	protected function setbookname(){
		return $this->bookname = 'php 1st edition';
	}

}

class author extends books{
	 public function getbookname(){
		return $this->setbookname();
	}
}

$object = new author();
echo $object->getbookname();
//output : php 1st edition
```


## 4- Magic Functions  | Construct and Destruct
what is magic functions?
magic functions are functions that start with double underscore before their name.
- constructor is function that runs when object of class is created and doesn't have return type (means doesn't return value),but if you use its function name it can return the value
- destruct is function that runs at the end when object of class is created , doesn't have return type.


- [ ] i-  construct method code.
- normal construct function: if construct function is writing this way its not possible to return its value by using return keyword , because it a part of the object.
```php
class books{
	public function __construct(){
		echo "helo from construct function/method";
	}

}
//create instance of class
echo $object = new books();
//output : helo from construct function/method
```

- construct function return value.
construct function can return value by calling its function name.
```php
class books{
	public function __construct(){
	 $data = 'helo world';
	 return $data;
		
	}
	
}
//create instance of class
$object = new books();
echo $object->__construct();
//output : helo world.
```

- [ ] ii- Destruct method code below.
	- deconstruct is method that runs after the construct . code below show how we can change the value of variable.
```php
class books{
	public $bookname;
	public function __construct(){
	 $this->bookname = 'php 1st edition';
		echo $this->bookname."\n";
	}
	
	public function __destruct(){
		$this->bookname = 'book name changed';
		echo $this->bookname."\n";
	}
	
}
//create instance of class
$object = new books();
//output : php 1st edition , book name changed

```

## 5- Inheritance
inheritance is object oriented concept and its ability to inherit or extend class content and use it inside another class.
below is code example.
```php
// is this example we will create to class , classone we will called author and classtwo we will called books , we will tru to extand author class information and display it inside book class.

class author{
	public $authorname = 'MuradCade';
	

}

class books extends author{
		public $bookname = 'php 1st edition';
		public function displayauthorandbookname(){
			return "bookname : ".$this->bookname.' is authered by '.$this->authorname;
		}
}

// create instance of class named books
$object = new books();
echo $object->displayauthorandbookname();
//output : bookname : php 1st edition is authered by MuradCade
```


## 6- Getters and Setters
when a method or property has access specifier of private or protected , to access their value  or give a value we use getters and setters.
code below is example of getters and setters.

```php
// let create class called users , this class will two property , one with private modifier and the other with protected modifier.

class users{
	private $name;
	protected $age;
	
	
// setter(setnameandage) method will handle givig value to private and protected properties.

	public function setnameandage($name,$age){
		$this->name = $name;
		$this->age = $age;
		
	}
	
	// getter(getnameandage) method that will return the value of name property.
	public function getnameandage(){
		return 'name : '.$this->name.", age: ".$this->age."\n";
	}
	
}

//create object of class users
$object = new users();
$object->setnameandage('murad','01');
echo $object->getnameandage();
//output: name : murad, age: 01
```


##  7- Type Decoration / Type Hinting
Type decoration or Type hinting is way to define variable data type, imagine we have function called addition(a,b) that takes to integer values as parameter , when 2 values argument expected to be integer but the passed argument is string how can we check that and display error.
Type decoration is a way to give function specific data type variable and display error if expected doesn't match the type given in parameter.
code below explain it.

```php
//lets create function named addition that takes two parameter as integer number and if something else is given display error.
//declare function says every function will only takes specify data type
declare(strict_types = 1);
function addition(int $a,int $b){
 $result = $a+$b;
return $result;
}
echo addition(2,2);
//output : 3
//if you give string add('1','2') it will display error


```
