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

# Consume using container-to-container networking
To use Cloud Foundry's container networking (see Container-to-container networking)[https://docs.vmware.com/en/Spring-Cloud-Services-for-VMware-Tanzu/3.2/spring-cloud-services/GUID-service-registry-writing-client-applications.html#consume-using-c2c] to reach an app registered with the Service Registry, you must add a network policy. You can do this using the Cloud Foundry Command Line Interface (cf CLI).

**Note:**
Container networking support is included in the cf CLI version 6.30.0 and later.

Run the cf network-policies command to list current network policies:

```bash
$ cf network-policies
```

Listing network policies in org myorg / space dev as user...
```bash
source   destination   protocol   ports
Use the cf add-network-policy command to grant access from the Greeter app to the Messages app:
```

```bash
$ cf add-network-policy greeter --destination-app greeter-messages --protocol tcp --port 8080
Adding network policy to app greeter in org myorg / space dev as user...
OK
Use cf network-policies again to view the new access policy:
````

```bash
$ cf network-policies
```

Listing network policies in org myorg / space dev as user...

source    destination          protocol   ports
greeter   greeter-messages   tcp        8080
The Greeter app can now use container networking to access the Messages app via the Service Registry. For more information about configuring container networking, see Administering Container-to-Container Networking.

