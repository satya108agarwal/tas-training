# CPU entitlement

CPU entitlement is the percentage of host CPU a particular app instance is entitled to use. The cpu_entitlement metric shows that apps have a CPU performance of 100% when they are using exactly the CPU they are entitled to. Apps have a CPU performance of less than 100% when their usage is less than their entitlement and greater than 100% when they are higher than their entitlement.

In TAS for VMs, apps have CPU entitlements that are proportional to their allocated memory, by default. For example, an app with access to 256MB of memory on a 512MB machine has access to half of the memory on the machine and is also entitled to half of the CPU of that machine.

## Spare CPU resources and throttling
If there are three cores on the Diego Cell to which your app is deployed, 300% CPU can be distributed among all the apps on the Diego Cell. This is the percentage that the cf app command displays. The metrics depend on factors such as the capacity of the Diego Cell and the total number of apps on it that are not visible to the user. This can make it difficult for you to balance CPU resources.

An app always receives 100% of its CPU entitlement, no matter what other apps are on the Diego Cell. If there are spare resources on the machine, an app can consume over 100% CPU.

CPU burst optimization is turned off by default. Go to the App Containers tab and select Allow CPU burst optimization.

**Without CPU burst optimization**
When CPU Burst Optimization is turned off, all apps on the cell share any spare CPU resources.

**With CPU burst optimization**
When CPU Burst Optimization is turned on, “good” apps get bursting priority over “bad” apps. Good apps are apps that, on average, stay within their CPU entitlement. Bad apps are apps that, on average, exceed their CPU entitlement.

For example, a Diego Cell with 5 bad apps and 1 good app. Initially the 5 “bad” apps split all of the spare CPU resources evenly. If the good app needs to burst, it is given priority for all the extra CPU it needs. If the good app continues bursting for long enough, and on average it exceeds its CPU entitlement, then it becomes a bad app. Then all 6 “bad” apps share the spare CPU resources equally. Likewise, if one of the bad apps stops using so much CPU it becomes a good app again.
