# TAS Training
## CF Login and Setup Orgs and Spaces


### CF Cli Install - Mac
```
For mac use below 
brew install cloudfoundry/tap/cf-cli@7

Refer documentation
https://docs.vmware.com/en/VMware-Tanzu-Application-Service/6.0/tas-for-vms/install-go-cli.html

```

### PCF Authentication
```
cf api <<pcf api url>>
cf login --sso
  # Go visit web browser and paste in code your!
  Temporary Authentication Code ( Get one at https://login.sys.dhaka.cf-app.com/passcode ): ....
```

### Setup Orgs and Spaces
```
export ORG_NAME="myorg"
export SPACE_NAME="development"
cf create-org "$ORG_NAME"
cf target -o "$ORG_NAME"
cf create-space "$SPACE_NAME"
cf target -s "$SPACE_NAME"
```

### Use GUI To create orgs and Spaces



