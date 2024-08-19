## laravel

### artisan

#### server
```
// in default port server is 8000
home php artisan serve

// add your port
home php artisan serve --port=9000 
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
```