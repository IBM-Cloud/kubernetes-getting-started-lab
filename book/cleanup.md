# Remove resources

* Delete the app `ibmcloud dev delete`
* Remove the Kubernetes artifacts created for the application `helm delete --purge <appname>`
* Delete the [LogDNA service](https://cloud.ibm.com/observe/logging).
* Delete the [Sysdig service](https://cloud.ibm.com/observe/monitoring).
  
