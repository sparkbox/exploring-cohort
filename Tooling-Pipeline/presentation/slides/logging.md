# Logging


## Rollbar
We use Rollbar for 2 main purposes


### Error Logging
![Screenshot of error logs](../images/rollbar-error-logs.png)


### Monitoring Deploys
![Screenshot of deploy logs](../images/rollbar-deploy-logs.png)


## Requirements
  * Your code should send error/warning messages to Rollbar with meaningful data.
  * Rollbar should be notified whenever you deploy a new version
  