# Deploy an spring application

Steps: Clone below repo and follow the steps in readme

```
git clone git@github.com:satya108agarwal/springrestapp.git
```

Summary of CF Commands Learnt So far:
```
cf push
cf apps
cf delete springrestapp -f
cf logs springrestapp
cf restage springrestapp
cf restart springrestapp
```

Restage (cf restage): Redeploys the application without changing its configuration, useful for refreshing the application's build or fixing potential issues related to the application droplet.

Restart (cf restart): Completely stops and starts the application instances, suitable for applying configuration changes or updating dependencies that require a clean start.
