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