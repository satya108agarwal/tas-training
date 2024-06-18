


# Deploy an spring data jpa mysql application

Steps: Clone below repo and follow the steps in readme

```
git clone [git@github.com:satya108agarwal/springrestapp.git](https://github.com/satya108agarwal/spring-data-jpa-mysql.git)
```

Summary of CF Commands Learnt So far:
```
cf create-service p.mysql db-small mysql-service
cf bind-service springdatamysql mysql-service
cf env springdatamysql
```
