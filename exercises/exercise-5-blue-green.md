# Introduction to Deployment Strategies
Deployment strategies are methodologies for releasing new versions of software applications into production environments. Each strategy offers distinct advantages in terms of minimizing downtime, reducing risk, and ensuring seamless updates. Common deployment strategies include:

**Rolling Deployment:** Gradual update of application instances in a rolling fashion, ensuring continuous availability by replacing old instances with new ones incrementally.

**Canary Deployment:** Incremental release of new versions to a subset of users or traffic segments to validate performance and gather feedback before a full rollout.

**Blue-Green Deployment:** Simultaneous deployment of two identical production environments (blue and green). Traffic is routed to one active environment while the other remains inactive, facilitating zero-downtime updates and easy rollback if issues arise.

# Blue-Green Deployment: Why It's Popular
Blue-Green deployment is favored for its ability to minimize downtime and risk during deployments:

**Zero Downtime:** By maintaining two identical environments, traffic can be seamlessly switched from one (blue) to the other (green) with no interruption in service.

**Rollback Capability:** If issues are discovered in the green environment after deployment, reverting to the blue environment is straightforward and immediate.

**Testing in Production:** It allows for rigorous testing of new releases in a production-like environment (green) while the blue environment handles production traffic.

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
