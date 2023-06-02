# gRPC Telemetry Troubleshooting for Cisco Wireless IOS XE devices #

## This guide will help you to troubleshoot and identify where the issue might be with gRPC and the subscriptions ##

## Let's get the show tech and archive files from the controllers: ##
```
term len 0
show tech-support wireless
show tech
request platform software trace archive last <days>
```

## Now, it's time to verify that the requisite processes (particularly pubd) are running: ##
```
show platform software yang-management process
```
## Verify the Memory CPU utilizando of Pubd process (process used by grpc). Make sure to run the command few times: ##
```
show processes cpu platform sorted | i pubd
show processes memory platform sorted | s pubd
```
## Make sure capture and validate the configuration specific to telemetry: ##
```
show running-config | section telemetry
```
## Check the validation of all subscriptions: ##
```
show telemetry ietf subscription all
```
## Let's verify the validation of any named receivers: ##
```
show telemetry receiver all
```
## Verify the profile and receiver name associated to the connection: ##
```
show telemetry receiver all
```
## Verify the total number of subscriptions configured in the device: ##
```
show telemetry ietf subscription summary
```
## Verify the total number of subscription per collectors/load-balancer: ##
```
show telemetry connection <index> detail
```
## It's good to Check which subscriptions use a particular connection: ##
```
show telemetry connection <index> subscription
```
## Let's verify the telemetry subscriptions states: ##
```
show telemetry internal subscription all stats
```
## It's good to also check the state of the subscription receiver: ##
```
show telemetry ietf subscription <id> receiver
```
or
```
show telemetry ietf subscription all detail
```
## Collect the general telemetry diagnostics: ##
```
show telemetry internal diagnostics
```
