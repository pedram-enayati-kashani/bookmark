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