
- **cf routes**: Lists all routes configured in the current Cloud Foundry organization and space, showing mappings between routes and applications.
- **cf domains**: Displays registered domains within Cloud Foundry, essential for mapping routes to applications with appropriate URLs.
- **cf map-route springdatamysql apps.dhaka.cf-app.com --hostname springdata**: Maps `apps.dhaka.cf-app.com` to the `springdatamysql` application under hostname `springdata`, directing traffic accordingly.
- **cf app springdatamysql**: Provides detailed status and configuration information for the `springdatamysql` application, including its routes and current resource usage.
- **cf unmap-route springdatamysql apps.dhaka.cf-app.com --hostname springdatamysql**: Removes the route mapping from `apps.dhaka.cf-app.com` with hostname `springdatamysql`, updating the application's routing configuration.
- **cf app springdatamysql**: Retrieves updated details about the `springdatamysql` application post-unmapping, verifying the route's removal and current application status.



### Commands learnt so far
```
   cf routes
   cf domains
   cf map-route springdatamysql apps.dhaka.cf-app.com --hostname springdata
   cf app springdatamysql
   cf unmap-route springdatamysql apps.dhaka.cf-app.com --hostname springdatamysql
   cf app springdatamysql
```
