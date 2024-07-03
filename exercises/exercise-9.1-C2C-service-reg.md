# Register using container-to-container networking

To use Cloud Foundry's container networking [Container to Container Networking](https://docs.vmware.com/en/VMware-Tanzu-Application-Service/6.0/tas-for-vms/understand-cf-networking.html) with the app, your application.yml must specify a spring.cloud.services.registrationMethod of direct.
```yaml
spring:
  application:
    name: greeter-messages
  cloud:
    services:
      registrationMethod: direct
```

Before a client app can use the Service Registry to reach this directly-registered app, you must add a network policy that allows traffic from the client app to this app. See the Consume Using (Container-to-Container)[https://docs.vmware.com/en/Spring-Cloud-Services-for-VMware-Tanzu/3.2/spring-cloud-services/GUID-service-registry-writing-client-applications.html#consume-using-c2c] Networking section for more information.

