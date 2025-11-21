# laravel

## version 5.8
```php
composer create-project --prefer-dist laravel/laravel blog "5.8.*"

```

### artisan

#### server

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

#### fresh and refresh

```php
$user = User::where('id',4)->get()->first();

$freshUser = $user->fresh(); //Creates a new instance of the user model.

$refreshUser = $user->refresh(); //The created sample will be returned to the previous one.

```

#### $guarded and $fillable
**guarded** is a protected variable that you can with it specify what can't user register

**fillable** is a protected variable that you can with it specify what can user register
```php
protected $guarded = [];

protected $fillable = [];
```

#### Query Scopes
make your method for modal
```php
// static
// in modal
public function scopeActive($query){
    return $query->where('status',1);
}

// in controller
public function index()
{
    $posts = Post::active()->get();
    dd($posts);
}

// dynamic
// in modal
public function scopeActive($query,$status){
    return $query->where('status',$status);
}

// in controller
public function index()
{
    $posts = Post::active(0)->get();
    dd($posts);
}
```

#### Accessors & Mutators
with Accessors you can create a method in your model and edit your data from database
```php
// in modal
// Accessors get
public function getLastNameAttribute($value){
    return $value ?: "No Last Name";
}

// in controller
$user = User::where('id',2)->first();
dd($user->last_name);  // getLastNameAttribute change to last_name

// example 2
// in modal
public function getFullNameAttribute(){
    return $this->first_name.' '.$this->last_name;
}

// in controller
$user = User::where('id',2)->first();
dd($user->full_name);  // getFullNameAttribute change to full_name

// example 3
// set Mutators
// in modal
public function settFirstNameAttribute($value){
    return $this->attribute['first_name'] = strtolower($value);
}

// in controller
$user = new User;
$user->first_name = 'PEDRAM';
$user->password = '12346';
$user->save();

```

#### casts
for specify some value of database you can use casts to specify value type
```php
// in modal
protected $casts = [
    'status' => 'string',
]
```

#### Relationships
```php
// one to one
// user modal
public function address(){
    return $this->hasOne('App\Address'); 
}

// address modal
public function user(){
    return $this->belongsTo('App\User'); 
}

public function user(){
    return $this->belongsTo('App\User','Owner_id','other_key'); // Owner_id like user_id and other_key like id user modal
}

// controller
$address = Address::find(1);
dd($address->user);

$user = User::find(82);
dd($user->address);

// one to many
// Comment modal
public function post(){
    return $this->belongsTo('App\Post'); 
}

// Post modal
public function comment(){
    return $this->hasMany('App\Comment'); 
}
// controller
$post = Post::has('comments')->get(); // get posts that has comment
dd($post);

// when some comment doesn't post_id you can set post_id with associate
$comment = Comment::find(4);
$comment->post()->associate(Post::first());
$comment->save();
dd($comment);

// when some comment does post_id you can null post_id with dissociate
$comment = Comment::find(4);
$comment->post()->dissociate();
$comment->save();
dd($comment);

// hasOneThrough This is used when you want to use one model as an intermediary to reach another model.
// you make a cars table
SchemaLLcreate('cars',function (Blueprint $table){
    $table->bigIncrements('id');
    $table->string('name');
    $table->bigInteger('user_id')->unsigned()->index();
    $table->timestamps();

    $table->foreign('user_id')->references('id')->on('users')->onDelete('cascade')->onUpdate('cascade');
});
// you make a information table
SchemaLLcreate('informations',function (Blueprint $table){
    $table->bigIncrements('id');
    $table->string('name');
    $table->bigInteger('car_id')->unsigned()->index();
    $table->timestamps();

    $table->foreign('car_id')->references('id')->on('cars')->onDelete('cascade')->onUpdate('cascade');
});

// in modal informations
protected $table = 'informations'; // for understand modal name of table

// in modal user
public function info(){
    return $this->hasOneThrough('App\Information','App\Car'); // the second one has the status of an intermediary.
}

// in controller
// user->car->info we want info through of car
$user = User::find(5);
dd($user->info)

// one to many
// make form table post tag
 SchemaLLcreate('post_tag',function (Blueprint $table){
    $table->bigInteger('post_id');
    $table->bigInteger('tag_id');
    $table->timestamps();

    $table->foreign('post_id')->references('id')->on('posts')->onDelete('cascade');
    $table->foreign('tag_id')->references('id')->on('tags')->onDelete('cascade');
});

// in modal Tag
public function posts(){
    return $this->belongsToMany('App\Post');
}

// in modal Post
public function Tags(){
    return $this->belongsToMany('App\Tag');
}

// in controller
$tag = Tag::find(1);
dd($tags->post);
$post = Post::find(125);
dd($post->tags);

// attach add to data
$post = Post::find(122);
dd($post->tags()->attach(1));
dd($post->tags()->attach([1,2]));
// sync remove old data and make a new data
dd($post->tags()->sync(2));
// detach remove data
dd($post->tags()->detach(2));

// if you want add a pivot
// in modal Post
public function Tags(){
    return $this->belongsToMany('App\Tag')->withPivot('value'); // value is a row in table post_tag
}

// in controller
dd($post->tags->first()->pivot->value);

// get pivote created at and updated at
public function Tags(){
    return $this->belongsToMany('App\Tag')->withTimestamps();
}
```

#### Polimorfig
We use polymorphic when we want to use a model in multiple or modal ways.
```php
// one to one
// make table image
 SchemaLLcreate('images',function (Blueprint $table){
    $table->bigIncrements('id');
    $table->string('url');
    $table->integer('imageable_id');
    $table->string('imageable_type');
    $table->timestamps();
});

// model Image
public function imageable(){
    return $this->morphTo();
}

// model post
public function image(){
    return $this->morphOne('App\Image','imageable');
}

// model user
public function image(){
    return $this->morphOne('App\Image','imageable');
}

// controller
$post = Post::find(124);
dd($post->image);
$user = User::find(124);
dd($user->image);
$image = Image::find(2);
dd($image->imageable);

// one to many
// make table videos
 SchemaLLcreate('videos',function (Blueprint $table){
    $table->bigIncrements('id');
    $table->string('title');
    $table->string('url');
    $table->timestamps();
});

// make table comments
 SchemaLLcreate('comments',function (Blueprint $table){
    $table->bigIncrements('id');
    $table->text('body');
    $table->integer('commentable_id');
    $table->string('commentable_type');
    $table->timestamps();
});

// model comment
public function commentable(){
    return $this->morphTo();
}

// model post
public function comments(){
   return $this->morphMany('App\Comment','commentable');
}

// model video
public function comments(){
   return $this->morphMany('App\Comment','commentable');
}

// controller
$post = Post::find(122);
dd($post->comments);
$video = Video::find(1);
dd($video->comments);
$comment = Comment::find(1);
dd($comment->commentable);

// create and save polimorfig

$post = Post::find(122);
$comment = new Comment;
$comment->body = 'bah bah';
$post->comments()->save($comment);

// many to many
// make table tagable
 SchemaLLcreate('tagables',function (Blueprint $table){
    $table->integer('tag_id');
    $table->integer('taggable_id');
    $table->string('taggable_type');
    $table->timestamps();
});

// model post
public function tags(){
   return $this->morphToMany('App\Tag','taggable');
}

// model Video
public function tags(){
   return $this->morphToMany('App\Tag','taggable');
}

// model tag
public function posts(){
   return $this->morphedByMany('App\Post','taggable');
}

public function videos(){
   return $this->morphedByMany('App\Video','taggable');
}

// controller
$post = Post::find(122);
dd($post->tags);

$video = Video::find(1);
dd($video->tags);

$tag = Tag::find(1);
dd($tag->videos);
dd($tag->posts);
```

#### Eager Loading

```php
// Comment modal
public function post(){
    return $this->belongsTo('App\Post'); 
}

// Post modal
public function comments(){
    return $this->hasMany('App\Comment'); 
}

$posts = Post::with('comments')->get();
$posts = Post::with(['comments','author'])->get();
$posts = Post::withCount(['comments'])->get();
$posts = Post::with(['comments','comment.user'])->get(); // get user that create comment
$posts = Post::with('comments:is,body',)->get();
$posts = Post::with(['comments'] => function($query){
    $query->where('id',1);
})->get();
dd($posts)
// Easy Eager Loading
$posts = Post::all();
if($someCondition){
    $posts->load('comments');
}

$posts->loadMissing('comments'); // if comments didn't load load comments
```

### test
```command
php artisan make:test PostTest -- unit // create test file
vendor/bin/phpunit // run test
```

```php
// example 1
public function test_post_exist()
{
    $this->assertDatabaseHas('posts',['user_id'=>288]); // check if a record exist
}

// example 2
// User modal
public function getFullNameAttribute(){
    return $this->first_name.' '.$this->last_name; 
}

// go to test file
public function test_full_name_accessor_works()
{
    $user = factory(User::class)->make([
        'first_name' => 'علی',
        'last_name' => 'کریمی',
    ]);

    $this->assertEquals('علی کریمی',$user->fullName); // check if full name Equal to علی کریمی or not
}

// example 3
public function test_relation(){
    $comment = factory('App\Comment')->create([
        'body'=> 'nice',
        'post_id'=>rand(1,100);
    ]);

    $this->assertInstanceOf('App\Post',$comment->Post); // check if a relation exist between Post and Comment
}
```

### laravel Mix
 ```
npm run watch // for make package

npm run production //for minify
```

### message bag
```php
public function index() {
    $messages = [
        'errors' => [
            'something went wrong',
        ],
        'messages' => [
            'create successful'
        ]
    ];
    $messagebag = new \Illuminate\Support\MessageBag($messages);
    if($messagebag->has('errors')){
        dd($messagebag->get('errors'));
    }
    return view('welcome')->withErrors($messagebag);

    // example 2
    $error = new \Illuminate\Support\MessageBag();
    $error->add('error','something went wrong');

    return view('welcome')->withErrors($error);

    // example 3
    return view('welcome')->withErrors(['error','something went wrong']);
}

// view file
{{ dd($errors) }}
```

### HTTP Requests
```php
// post controller
public function index(Request $request){
    dd($request->path()); // show your path route
    dd($request->is('post')); // check if in url exist post
    dd($request->is('post/*'));
    dd($request->url()); // show your url
    dd($request->fullUrl()); // show your url and your query
    dd($request->method()); // show your method
    dd($request->isMethod('get')); // if your method is get
    dd($request->all()); // show all of sended input
    dd($request->input()); // show all of sended input
    dd($request->input('name')); // show name of sended input
    dd($request->input('name.0.firstName'));
    dd($request->input('name','pedram')); // set a default value for name
    dd($request->name); // show value of name
    dd($request->only('name')); // only give you value of name
    dd($request->only(['name','last_name'])); // only give you value of name and last_name
    dd($request->except('_token')); // give you all filed except _token
    dd($request->has('name')); // if exist name filed
    dd($request->filed('name')); // check if filed not empty

    // file
    dd($request->file()); // show your file
    dd($request->file('image')); // show your file image
    dd($request->hasFile('image')); // your file image exist boolean
    dd($request->file('image')->isValid()); // is your file image uploaded boolean
}

// in view
{{ request()->path() }} //show your path route
```

### File Upload

```php
// post controller
public function index(Request $request){
    $request->image->move(public_path('uploads'),time().'.'.$request->image->extension());
}
```

### Validator
```php
// post controller
public function store(Request $request){
    $validator = Validator::make($request->all(),[
        'title'=>'required|min:5',
        'user_id'=>'required',
    ]);
    if($validator->fails()){
        return redirect()->back()->withErrors($validator);
    }

    Post::create($request->all());
    
    // example 2 
    $validator = Validator::make($request->all(),[
        'title'=>'required|min:5',
        'user_id'=>'required',
    ],[
       'title.required' => 'ok', // create error message
    ])->validate(); // do redirect

    Post::create($request->all());

    // example 3
    $request->validate([
        'title'=>'required|min:5',
        'user_id'=>'required',
    ]);

    Post::create($request->all());
}

// views file
@if($errors->any())
    @foreach($errors->all() as $error)
        {{$error}}
    @endforeach
@endif
```

**point :** if you want you error message become persian add fa to resources->lang directory and put fa lang after that go to config->app.php make
```php
'local'=>'fa',
```

#### custom validation
```php
php artisan make:rule Uppercase // create file Uppercase in app->Rules

// Uppercase.php
public function passes($attribute,$value){
    return strtoupper($value) === $value;
}

public function message(){
    return 'باید با حروف بزرگ نوشته شود';
}

// postController
    $request->validate([
        'title' => ['required',new Uppercase],
        'book.id' => 'required', // validation array
        'book.name' => 'required',
    ]);
```

#### Request
```
php artisan make:request storePostRequest
```

```php
// in file storePostRequest
public function authorize()
{
    return false // make true
}

public function rules()
{
    return [
        'title' => 'required|min:5',
    ]
}

// post controller
public function store(Request $request){
    Post::create($request->all());
}
```

#### test
```php
    public function test_input_missing_a_title_is_rejected()
    {
      $response = $this->post(route('post.store'), ['title' => 'test title']);
      $response->assertRedirect();
      $response->assertSessionHasErrors();
    }

    public function test_valid_input_should_create_a_post_in_the_database()
    {
        $this->post(route('post.store'), ['title' => 'title2', 'user_id' => 295]);
        $this->assertDatabaseHas('posts', ['title' => 'title2', 'user_id' => 295]);
    }
```

### Authentication
```php
php artisan make:auth // with this command you can create view auth, edit user model and edit home controller add auth controller
```

### Middleware
```php
php artisan make:middleware checkAge // after create middleware you must register middleware in app/http/kernel.php 
```