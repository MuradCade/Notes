today we will learn object oriented concept specifically in PHP.
in order to understand object oriented we will discuss the following concepts:-
- [ ] Class and Objects ,
- [ ] Method (function) and Properties (variables)
- [ ] Access Modifiers in Properties and Methods




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
	
## Methods and Properties Explained
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
```

- code above shows us that we can access property value directly outside class or we can use method to return the value of property

## Access Modifiers in Properties and Methods Explained
what is access modifiers?

