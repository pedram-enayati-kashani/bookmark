## laravel

### artisan

#### server
```
// in default port server is 8000
php artisan serve

// add your port
php artisan serve --port=9000 

// show all of route created in your project
php artisan route:list
```

#### migratian
```
// install migration database
home php artisan migrate
```
---
#### app key
```
// this command generate app key
home php artisan key:generate
```

#### Facade
facade is mean structure view
```php
Route::get();
```

#### Route
laravel route Method has Get,Post,Put,Delete,Match,any

```php
Route::get('/',function (){
    return view('welcome');
});

// this Route match is get route method get and post
Route::match(['get','post'],'/',function (){
    return view('welcome');
});

// this Route match is get any route method that set with this address
Route::any('/',function (){
    return view('welcome');
});

// add id or value to route
Route::any('/{id}',function ($id){
    return $id;
});

// id is optional can exist or not
Route::any('/{id?}',function ($id = 1){
    return $id;
});

// add regular expression to route with method where
Route::get('/{id}',function ($id){
    return $id;
})->where('id','[1-9]');

// if route in your web doesn't exist this route activate
Route::fallback(function (){
   return 'hi';  
});

// add controller to Route
Route::get('/', [HomeController::class, 'index']);

// it make all CRUD route 
Route::resource('photos', PhotoController::class);
```

#### view
```php
Route::get('/',function (){
    //return view('welcome')->with('var','test');
    // return view('welcome',['var'=>'test']);
    return view('welcome',compact('var'));
});
```

#### Controller
```php
php artisan make:controller NameController /* create controller with command */

php artisan make:controller NameController --resource /* this command create a controller for CRUD */

php artisan make:controller NameController --invokable /* this command create a controller for performs one action */
```

#### all http method
```
get
post
put : for update all model
patch : for update attribute
delete
```

#### Helper Method
```php

    dd($value) /* show all value and info in variable */

    abort(404,'message for error') /* make a error */
```

#### error view
with bottom command you can access to error view in views directory
```
php artisan vendor:publish --tag=laravel-errors
```

#### write test
**it has two directory**
* feature : test for big project
* unit : test for small project

```php
php artisan make:test UserTest /* command create test */
./vendor/bin/phpunit /* run php unit */
./vendor/bin/pest /* run php unit */
./vendor/bin/pest --filter firstTest /* run special test */
```