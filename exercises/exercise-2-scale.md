# Scaling 
## Horizontal Scaling
Horizontal scaling involves adding more instances (or replicas) of an application to handle increased load or improve availability. 
Cloud Foundry makes it straightforward to scale applications horizontally using the cf scale command.

```
cf scale springrestapp -i NEW_INSTANCE_COUNT

```

## Viewing Current Instances
To view the current number of instances:

```
cf app springrestapp
```

## Vertical Scaling

```
cf scale springrestapp -m NEW_MEMORY

```
Note: Causes the app to restart. 
