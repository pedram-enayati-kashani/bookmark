## **function**

#### **str_replace()**
this function get three parameter first the word you want to find second the word you want to replace third is the data
```php
$data = "hello world";
$str= str_replace("world" , "peter" , $data);
out = hello peter
```

#### **explode()**
this function get three parameter first the separator character that you want to break a sting two data third limit
```php
$data = "hello world";
$str= explode(" " , $data);
out = {
    "hello",
    "world,
}
```

#### **dirname()**
return parents path
```php
echo dirname("c:/testweb/home.php") . "<br />";
echo dirname("c:/testweb/home.php",  2) . "<br />";
out =
c:/testweb
c:
```

#### **realpath()**
return path file
```php
echo realpath("test.txt");
out = C:/Inetpub/testweb/test.txt
```

#### **ReflectionMethod()**
return report information about class
```php
$reflection = new ReflectionMethod($class , $method)
```

#### **method_exists()**
it's check your method in your class exist or not
```php
method_exists($class , $method)
```

#### **call_user_func_array()**
it find your method from class and calls
```php
call_user_func_array($class , $method)
```

#### **strpos()**
return postion value in sentens
```php
$str = "find something better";
strpos($st , 'find');
out : 0
```

#### **stripos()**
return like strpos but in insensitive
```php
$str = "find something better";
strpos($st , 'betterd');
out : 15
```

#### **compact()**
it's get some variable parametre and retun every parametre in array 
```php
$color = "red";
$animal= 'cat',
$car="bmw";
compact('color' , 'animal' , 'car');
out : array (3){["color"] => string(3) "red" ["animal"] => string(3) "cat" ["car"] => string(3) "bmw"} 
```

#### **extract()**
it's get array and return variable
```php
$color = {"color" => "red" , "animal" => "cat" , "car" => "bmw"};
out : $color , $animal , $car
```

#### **sql_autoload_register()**
with this method you can chose to include one mehode in a class or you can load every methods in a class
```php
spl_autoload_register('MyAutoloader::ClassLoader');
spl_autoload_register('MyAutoloader::LibraryLoader');
spl_autoload_register('MyAutoloader');

class MyAutoloader
{
    public static function ClassLoader($className)
    {
         $path = '/path/to/class/';

        include $path.$className.'.php';
    }


    public static function LibraryLoader($className)
    {
         $path = '/path/to/class/';

        include $path.$className.'.php';
    }
}
```

### OPP Object-Oriented Programming
structure class php :
```php
class className {
    public function method(){

    }
}
```

#### Abstract classes
this mean we dont know how is class body we just reserve and where we need to use this class that time we create class body 
```php
abstract class Country{
    public $name

    function __construct($name){ 
        $this->name = $name;
    }

    abstract public function shoaar() : string;
}

class Iran extends Country{
    public function shoaar() : string{
        return 'Hi '.$this->name; 
    }
}
$iran = new Iran('Iran');
$iran->shooar();
```
**__construct :** when you call this class this methode called

#### Interface
this make a law for programmer to make programmer follow the law that admin manager created and methode  interface must be public type
```php
interface Animal{

    // public $name;
    public function eat();
}

class Cat implements Animal
{

    public function eat(){
        echo 'eat very fast';
    }

}

$cat = new Cat();
$cat->eat();
```
**implements :** this mean create body Animal

**define a value in class :**
```php
define("NAME" , $name);

class className{

    const Name = 'pedram';

    public static $color = 'black';

    public function name(){
        echo self::Name .' '. self::$color;

    }
}

echo className::name();
```
**self :** mean this
**parent :** call class that your class has extend

**example :** 
```php
interface Handler{
    public function setNext(Handler $handler): Handler; /* (Handler $handler) this mean you property in object of ypur class and (): Handler mean your output ,ust be object of ypur class in otherway this mean you say what type is your output*/
    public function handler(Handler $request): ?string; /* this mean your output can be string or null */
}

class className implements Handler{

    protected $query;

    public function reset(): void /* this mean your meathod dosen't has output */
    {
        $this->query = new \stdClass; /* this make a empty object */
    }
}
```



### PDO

#### **PDO::ATTR_ERRMODE**
with this we can chose how to show and what show in error
```php
PDO::ATTR_ERRMODE=> PDO::ERRMODE_EXCEPTION
```
#### **PDO::ATTR_DEFAULT_FETCH_MODE**
with this ypu can chose how to access to object
```php
PDO::ATTR_DEFAULT_FETCH_MODE=>PDO::FETCH_ASSOC
```

### ORM : Object Relational Mapping
this make a intermediary between sql and php with this you right a method with php and this method change your quest to sql command

### **Variable variables :**
```php
$this->a = "hello";
$this->b = "hi";
$this->val = "howdy";

$val = "a";
echo $this->{$val}; // outputs "hello"

$val = "b";
echo $this->{$val}; // outputs "hi"

echo $this->val; // outputs "howdy"

echo $this->{"val"}; // also outputs "howdy"

```