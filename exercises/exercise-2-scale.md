
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


# Setting Up Autoscaling for PCF Application

To automate scaling based on application metrics in Pivotal Cloud Foundry (PCF), follow these steps to configure autoscaling using either the Autoscaler service or `manifest.yml` file.

## Option 1: Using Autoscaler Service

### Step 1: Create Autoscaler Service Instance

```bash
cf create-service autoscaler PLAN_NAME AUTOSCALER_INSTANCE_NAME
```

## Step 2: Bind Autoscaler Service to Application
```bash
cf bind-service APP_NAME AUTOSCALER_INSTANCE_NAME
```

## Step 3: Using Manifest File
Step 1: Update Manifest File (manifest.yml)
```yaml
applications:
  - name: springdatamysql
    memory: 1G
    instances: 1
    path: build/libs/springdatamysql.jar  # Path to your Spring Boot application JAR
    buildpacks:
      - java_buildpack_offline
    services:
      - mysql-service
    env:
      JBP_CONFIG_OPEN_JDK_JRE: '{ jre: { version: 17.+ } }'
    autoscaling:
      min_instances: 2
      max_instances: 5
      enable_cpu: true
      cpu_threshold: 70
      cooldown: 120
```
In this example:

**min_instances** : Minimum number of instances.
**max_instances**: Maximum number of instances.
**enable_cpu**: Enable CPU-based autoscaling.
**cpu_threshold**: CPU threshold percentage for scaling actions.
**cooldown**: Cooldown period (in seconds) between scaling actions.

## Step 4: Deploy Application
```bash
cf push
```
