
## Steps to create Blue Green Deployment using routes.

### Step 1: Clone
```
git clone git@github.com:satya108agarwal/springrestapp.git
```
### Step 2: Change the app name to blue, build,deploy and check the status of the application

```
   ./gradlew clean build
   cf push
   cf app springrestapp-blue
   cf map-route springrestapp-blue apps.dhaka.cf-app.com --hostname prod
```
### Step 3: Prod is now pointing to blue version of the code base

Modify the code to change it to green, build, deploy and check the status of the green version of application

```
   ./gradlew clean build
   cf push
    cf app springrestapp-green
```

### Step 4: Unmap the route to blue and map it to green
```
   cf unmap-route springrestapp-blue apps.dhaka.cf-app.com --hostname prod
   cf map-route springrestapp-green apps.dhaka.cf-app.com --hostname prod
```

### Step 5: Check the traffic is now routes to green app.
