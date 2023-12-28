## Attack to web include of :
#### xss , 

### to prevent xss you can add mthode htmlentities()
```php
$comment['comment'] == <script>alert('hi')</script>
htmlentities($comment['comment']);
```

##hijack session

this mean your session value token was stolen or being exposed with than token someone can login without put user and password in login form