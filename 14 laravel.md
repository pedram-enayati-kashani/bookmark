# laravel

## version 5.8

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

### Route
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
Route::get('/', 'HomeController@index');

// it make all CRUD route 
Route::resource('photos', 'PhotoController');

// it's like resource but don't make route get for update and create
Route::apiResource('photos', 'PhotoController');
```

### view
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

#### See All Of Your Route
```php
php artisan route:list
```

#### Redirect

```php
// helper
Route::get('redirect-with-helper', function(){
    return redirect()->to('category/create');
});

// shortcut
Route::get('redirect-with-shortcut', function(){
    return redirect('category/create');
});

// fasade
Route::get('redirect-with-fasade', function(){
    return Redirect::to('category/create');
});

// fasade
Route::redirect('redirect-with-fasade2','category');

// route name
Route::get('redirect', function(){
    return redirect()->route('category/create');
});

// route with parameter
Route::get('redirect', function(){
    return redirect()->route('category/create',['id'=>1]);
});

// route with parameter
Route::get('redirect', function(){
    return redirect()->back();
});

Route::get('redirect', function(){
    return redirect()->with("seesion name","value");
});
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
---

#### Local SEO
some time you want to make seo of some site that show it's address in that site you can set link in directory like guc site , form, google place,yahoo search, bing, ublo, ...

---

### @blade

#### forelse
```php
@forelse($users as $user)
    {{ $user }}
@empty
    {{ "no user }}
@endforelse
```

#### @extend()
mother layouts

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>@yield('title')</title>
    </head>
    <body>
        @yield('content')
        @yield('content2',view::make('view.name')) //with this you can pass a view in yield
        @section('script')
            <script>alert('hi')</script>
        @show
    </body>
</html>
```

#### @section and extends
Inheritance

```php
@extends('layout.master')
@section('title','test')

// in master layout section end with show but in Inheritance section end with endsection
@section('content')
    this is content
@endsection

@section('scripts')
    @parents
    <script>alert('hi2')</script>
@endsection
```

#### @include 
for add new section in Inheritance
```php
@section('content')
    this is content
    @include('error')
    @includeIf('error') //is check if file exist load file
    @includeWhen($boolean,'error') //is check if file exist load file
@endsection
```

#### @each
```php
@each("error",$projects,'project','error-none')
```

#### @json

```php
    <script>
        let app = <?php echo json_encode($array); ?>;
        let app = @json($array);
    </script>
```

#### @slot and @component

```php
    // Inheritance
    @component('layouts.partials.button')
        @slot('color')
            danger
        @endslot
        @slot('text')
            خطا
        @endslot
    some text
    @endcomponent
```

```php
    // component file
    <div class="">
        <button type="button" class="btn btn-{{ $color }}">{{ $text }}</button>
        <p>{{ $slot }}</p>
    </div>
```

#### @inject
with inject you can inject class to view
```php
@inject('car','App\Car');
```

#### make directive Blade
first go to provider in the boot write
```php
Blade::directive('ifGuest',function(){ //in provider
    return "<?php if(Auth()->guest()); ?>";
});

@ifGuest // in view

Blade::directive('like',function($like){ //in provider
    return "<?php if($like); ?>";
});

@like($like) // in view

```

### stack and push
```php
// master file

@stack('css')

// Inheritance file
@push('css')
 <link rel="stylesheet" href="example.css">
@endpush
```

### @prepend

```php
// master file

@stack('css')

// Inheritance file put in first line
@prepend('css')
 <link rel="stylesheet" href="example.css">
@prepend
```

### provider

```php
php artisan make:provider TestServiceProvider
```

### composer

```php
// provider file boot
// for register config\app.php
view()->composer('layouts.master',function($view){
    $view->with('count',5);
});

view->composer('layouts.master',\App\Http\View\Composers\TestComposer::class);

view->composer(['layouts.master','layouts.header'],\App\Http\View\Composers\TestComposer::class);

view->creator('layouts.master',\App\Http\View\Composers\TestComposer::class);


// TestComposer file
namespace App\Http\View\Composers;

use Illuminate\Contracts\View\View;

class TestComposer{
    public function composer(View $view){
        $view->with('count',5);
    }
}

```

### migration and data base
for config date base you go to the .env file part connection = mysql

```php
php artisan migrate // create all migration table in database

php artisan migrate::rollback // roll back one one step back

php artisan migrate::rollback --step=2 // chose the last two batch

php artisan migrate::status // show all of your migration with their status

php artisan migrate::reset // drop all of your migration

php artisan migrate::refresh // drop all of your migration and install all of your migration

php artisan migrate::fresh // drop all of your migration and install all of your migration

php artisan make:migration create_articles_table --create=articles // create a migration table

php artisan make:migration add_images_to_articles_table --table=articles // add or edit some thing in table
```

### Seeders and Factories
for create fake record on database
```php
php artisan make:seeder UsersTableSeeder // create face users

php artisan db:seed --class=UsersTableSeeder // run seeder class UsersTableSeeder

php artisan migrate --seed // run migrate and seed

php artisan make:factory PostFactory

```

**point :** if you want create persian fake name goto config/app.php and search faker_locale and edit
```php
"faker_locale" => "fa_IR"
```

### Modal

```php
php artisan make:modal Users
```