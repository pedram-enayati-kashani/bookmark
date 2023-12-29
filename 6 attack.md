## Attack to web include of :
#### xss , 

### to prevent xss you can add mthode htmlentities()
```php
$comment['comment'] == <script>alert('hi')</script>
htmlentities($comment['comment']);
```

##hijack session

this mean your session value token was stolen or being exposed with than token someone can login without put user and password in login form

sometime someone can with get session id whit write PHPSESSID in url get value session id to pervent this you can go to php.ini and change value session.use_strict_mode to 1
```php
session.use_strict_mode=0 change to 1
session.use_strict_mode=1 changed
```

##Methode Header
with this methode you can redirect your user to the you want user go
```php
header("Location: login.php");
```
with this your user redirect to login.php if you did't add die or exit after header your script after redirect can be run . right with web you can't see your script but if you send http request wth command line you can see your script with curl
```command
curl --include http://localhost/header/panel.php
```
to pervent this happening you need add exit or die but if you add die this is more secure

##csrf

the first thing you must do every link that you created with id in panel admin must change to form becuse it become method get and this less secure
example :
```html
<a href="article.php?id=1">delete</a>
change to
<form action="" method="post">
    <input type="hidden" value="1">
    <button type="submit">delete</button>
</form>
```

second create a token for your form
```php
<?php
    session_start();
    if(empty($_SESSION['token'])){
        $_SESSION['token'] = bin2hex(random_bytes(32));
    }
    $token= $_SESSION['token'];
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form action="article/delete" method="post">
        <input type="hidden" name="token" value="<?= $token ?>">
        <input type="hidden" name="id" value="1">
        <button type="submit">delete</button>
    </form>
</body>
</html>
```

##register_globals
this going to make key request post to varable this mean `$_POST['username']` == `$username` so you need to make value this method change to off in php.ini
```
register_globals= Off
```