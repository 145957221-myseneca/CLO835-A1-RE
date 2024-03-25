# Building and running 2 tier web application in ec2 using ECR images
### Building mysql docker image using ecr URI 
```docker pull URI-sql ```

### Building app docker image using ecr URI
```docker pull URI-app ```

### Running mysql
```docker run --name new_db --net Dnet1 -d -e MYSQL_ROOT_PASSWORD=password123 uri```

### Check all running Containers
```docker container ls -a ```

### Get the IP of the database and export it as DBHOST variable
```docker inspect <container_id>```


### Export env to run the applications (sql container ip)
```
export DBHOST=172.18.0.2
export DBPORT=3306
```
```
export DBUSER=root
export DATABASE=employees
export DBPWD=pw
```
### Run the application, make sure it is visible in the browser
```
docker run -d -p 8081:8080 \
-e DBHOST=$DBHOST -e DBPORT=$DBPORT \
-e DBUSER=$DBUSER -e DBPWD=$DBPWD \
-e APP_COLOR=blue --name blue \
uri
```
