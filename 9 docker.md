## *Architecture*:

* **monolithic architecture :** in this architecture your program has many features in one program
* 


### Docker :
image that you have multi module your program that module work in different service because of that you can't run every module on one setting but with docker you can run multi module in different container with their one setting 

---
#### docker command:

</br>

**pull :** this command download image in your docker 
```
docker pull ubuntu
```
</br>

**run :** this command run container in your docker 
```
docker run ubuntu
```
</br>

**sleep 10:** this command say execute container after 10 second in your docker 
```
docker run ubuntu sleep 10
```
</br>

**-it :** it mean run image in interactive
```
docker run -it ubuntu bash
```
</br>

**ls :** it show folder and file in container
```
ls 
```

</br>

**top :** it show info monitoring
```
top
```

</br>

**container ls :** show your container that has run
```
docker container ls
```

</br>

**container ls -a :** show history of your container that has run
```
docker container ls -a
```

</br>

**ps :** show process that has run
```
docker container ps
```

</br>

**ps -a:** show history of process that has run
```
docker container ps
```

</br>

**exec :** with this command you can login in container
```
docker container exec -it 7103fd6648b8(container id) bash
```

</br>

**exit :** with this command you can exit in command line container
```
exist
```

</br>

**stop :** with this command you can stop the running container 
```
docker container stop 7103fd6648b8
```

</br>

**images :** this command show your image
```
docker images
```

</br>

**rm :** this command delete your image
```
docker image --rm ubuntu
```

</br>

**rm -f:** this command delete your image by force
```
docker image --rm -f ubuntu
```

</br>

---

#### example
this command run all php content from D:/project/php and copy content this directory to /var/www/html
```
docker run -d -p 80:80 --name php -v D:/project/php:/var/www/html php:8.2.20-apache //php
docker run -d --rm --name mysql -e MYSQL_ROOT_PASSWORD=123456789 -e MYSQL_DATABASE=test -e MYSQL_USER=pedram -e MYSQL_PASSWORD=123456789 -p 3307:3306 mysql:latest //run mysql
docker run -d --name phpmyadmin -p 8080:80 --link mysql:db --rm phpmyadmin // run phpmyadmin
```

---

### docker file
docker file is a text file that has some programming instructions that use for create a image