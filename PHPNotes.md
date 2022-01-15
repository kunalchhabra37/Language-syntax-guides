# Funtions
- Reusable blocks of code.
- Variables scopes are in there namespaces.
- Variables are automatically deleted once there scope ends.
- We can call a function before declaring it.

```
function name(parameters){
	body
}
```

## Local Variables
- Local variables are variables that are created within a block/function.
- can only be accessed in it's scope.

## Global Variable
- Variables that can be accessed by whole program.
- There scope is program/script scope.
- It cannot be intialised at time of declaring it.

```
global $var_name;
```

## Static Variables
- Variables who are not deleted when their scope ends.
- They can only be accessed in their scope.
- It can also be initialised at time of declaring it.

~~~
Inside the scope:
static $var_name;
~~~

## SuperGlobal Variables
- They are provided by PHP.
- They can be used as Global Variables.
> **$GLOBALS** All variables that are currently defined in the global scope of the script. The variable names are the keys of the array.

> **$_SERVER** Information such as headers, paths, and locations of scripts. The entries in this array are created by the web server, and there is no guarantee that every web server will provide any or all of these.

> **$_GET** Variables passed to the current script via the HTTP GET method.

> **$_POST** Variables passed to the current script via the HTTP POST method.

> **$_FILES** Items uploaded to the current script via the HTTP POST method.

> **$_COOKIE** Variables passed to the current script via HTTP cookies.

> **$_SESSION** Session variables available to the current script.

> **$_REQUES** Contents of information passed from the browser; by default, [$_GET], [$_POST], and [$_COOKIE].

> [$_ENV] Variables passed to the current script via the environment method.

## Passing Arguments as Vaules
- It means a copy of Value is passed. So a change in reference variable won't effect the actual parameter.
- By default arguments are passed by Values.
- Unlike some languages like cpp, arrays are also passed by Value.

## Passing Arguments by Reference
- It means Reference of Variable is passed. So a change in reference parameter will effect the actual parameter.
- For passing argument by reference we have to put & before variables in function defination.
- It is Mandatory to pass only Variables and not Values as arguments at the time of calling a function.

```
function swap(&$a, &$b){
	code
}
```

## Default Values of Parameters
- We can add default values of parameters at the time of declaration of functions.
- Unlike other languages, it is not mandatory in php that default arguments shouldn't follow mandatory arguments, but it isn't a good practice to do so.

```
function name($first_name="ram"){
	code
}
```

## Variable Arguments
- If we don't know the number of arguments that are passed, we can declare them as variable arguments.
- Arguments will be passed as array.

```
function sum(...$numbers){
	code
}
```

> We shouldn't declare variable arguments before mandatory arguments.
- We can also pass arguments variabaly in php to save our time

```
sum(...[1,3,34,5]);
```

> In PHP we don't have function Overloading, but we have method overloading which is property of classes.
---
# Including and Requiring Files
## Include
- It helps to Include files in PHP scripts.

```
include "file.php";
```

- If we include same file more than once then php will give error. So we use include_once instead of include.
- include_once ignores all other inclusions of same file.

```
include_once "file.php";
```

## Require
- Problem with include is that, program will continue to execute efen when file not found.
- To solve this problem we use require..

```
require "file.php";
```

- Simillarly like include, we we can use required_once to include the file only one time.

```
require_once "file.php";
```

> We should make it a practice to always use require_once for including files.
---
# PHP Version Compatibility
- **phpinfo()** returns all the information about the version of php we are running.
- **function_exists()** checks all the built-in and user-defined functions.
- **phpversion()** returns the Version of PHP we are using.
---
# Object Oriented Programing 
- Object-Oriented Programming is a methodology or paradigm to design a program using classes and objects
- Classes: Templates for making obejcts
- Objects: It is the instance/occurance of that class.
- Features: Data Encapsulation, Data Abstraction, Inheritence, Polymorphism
- Methods: Functions used with an object.
- Prperties: Data associated with Object.

## Encapsulation
- Wrapping of code and data in single unit so that only objects methods can manipulate the data is called Encapsulation

## Inheritance
- We can create/derive another classes from already created class. This is known as Inheritance.
- Orignal class is called as Super Class and inherited class is called as derived class.

## Abstraction
- Abstraction is hiding the implemetation details and showing only functionality to the user.

## Polymorphism
- Ability of an Object to take many forms is known as Polymorphism.

## Declaring a Class

```
class Name{
	public $data;
	function name(){
		code
	}
}
```

## Creating new Object
- We can create Objects using new keyword
- To access properties and methods, $objet_name->attribute;
 
```
$var = new Name;
$var->data = "Kunal";
$var->name();
```

- print_r() helps to display us object in human readable format.
- Objects are always passed as Reference. 
- to create a copy of objects we need to use clone keyword.

## $this keyword
- It helps us to access the current objects Properties.

```
class Name{
	public $data;
	function name(){
		echo $this->data;
	}
}
```

## self:: Keyword
- We can access any constant propeties, static methods and static properties of object using self::name.

```
class Name{
	const $data;
	static $dt;
	self::dt = 1;
	self::data = 10;
	static function name(){
		code
	}
}
self::name();
```

## Constructor and Destructor
### Constructor
- **Constructor** is Special Class Method that initialises properties of class when Object is made.

```
class Name{
	public $name,$age;
	function __construct($name,$age){
		$this->name = $name;
		$this->age = $age;
	}
}
$object = new Name("ram",19);
```
- If we don't pass the value at time of creating object, It will give an error.
- to solve this, we can declare __construct() parameter's as default arguments.

```
class Name{
	public $name,$age;
	function __construct($name="NA",$age=0){
		$this->name = $name;
		$this->age = $age;
	}
}
$obj1 = new Name("ram",20);
$obj2 = new Name;  //No error and values initialised to "NA" and 0
```

### Destructor
- **Destructor** is also a special function that deletes or destroys an object when we call it or end of an program.

```
class Name{
	public $data;
	function __destruct(){
		destructor code;
	}
}
```

- If don't define destructor some bugs may arise.

## Class Scopes
- **public** - Public members can be referenced anywhere, including by other classes and instances of the object. This is the default when variables are declared with the var or public keywords, or when a variable is implicitly declared the first time it is used.
- **protected** - These members can be referenced only by the object’s class methods and those of any subclasses.
- **private** - These members can be referenced only by methods within the same class not by subclasses.

## Inheritence in Practice
-**extends** we use extends keyword to inherit classes

```
class Parent{}
class Child extends Parent{}
```

-**parent** When we override a method of parent class, to access that parent class method, we need to use parent:: keyword within the child class.

```
class Parent{
	function test(){
		code
	}
}
class Child extends Parent{
	function test(){
		code
	}
	function test2(){
		parent::test();
	}
}
```

- **Constructors** When extending the class, we have to explicitly call constructor of parent class inside the constructor of child class.

```
class Parent{
	public $dp;
	function __construct($dp){
		$this->dp = $dp;
	}
}
class child extend Parent{
	public $dc;
	function __construct($dp,$dc){
		parent::__construct($dp);
		$this->dc = $dc;
	}
}
```

- **final** It declares that a class or function cannot be override.

```
final function name(){
	code
}
```



