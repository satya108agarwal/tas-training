# Register using container-to-container networking

To use Cloud Foundry's container networking [https://docs.vmware.com/en/VMware-Tanzu-Application-Service/6.0/tas-for-vms/understand-cf-networking.html](see Container-to-Container Networking) with the app, your application.yml must specify a spring.cloud.services.registrationMethod of direct.
```yaml
spring:
  application:
    name: greeter-messages
  cloud:
    services:
      registrationMethod: direct
```
