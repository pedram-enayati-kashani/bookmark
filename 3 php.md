##**function**

####**str_replace()**
this function get three parameter first the word you want to find second the word you want to replace third is the data
```php
$data = "hello world";
$str= str_replace("world" , "peter" , $data);
out = hello peter
```

####**explode()**
this function get three parameter first the separator character that you want to break a sting two data third limit
```php
$data = "hello world";
$str= explode(" " , $data);
out = {
    "hello",
    "world,
}
```

####**dirname()**
return parents path
```php
echo dirname("c:/testweb/home.php") . "<br />";
echo dirname("c:/testweb/home.php",  2) . "<br />";
out =
c:/testweb
c:
```

####**realpath()**
return path file
```php
echo realpath("test.txt");
out = C:/Inetpub/testweb/test.txt
```

####**ReflectionMethod()**
return report information about class
```php
$reflection = new ReflectionMethod($class , $method)
```

####**strpos()**
return postion value in sentens
```php
$str = "find something better";
strpos($st , 'find');
out : 0
```

####**stripos()**
return like strpos but in insensitive
```php
$str = "find something better";
strpos($st , 'betterd');
out : 15
```

####**compact()**
it's get some variable parametre and retun every parametre in array 
```php
$color = "red";
$animal= 'cat',
$car="bmw";
compact('color' , 'animal' , 'car');
out : array (3){["color"] => string(3) "red" ["animal"] => string(3) "cat" ["car"] => string(3) "bmw"} 
```

####**extract()**
it's get array and return variable
```php
$color = {"color" => "red" , "animal" => "cat" , "car" => "bmw"};
out : $color , $animal , $car
```

####**sql_autoload_register()**
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

##PDO

####**PDO::ATTR_ERRMODE**

```php

```