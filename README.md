# app-sample
Sample Application based on https://github.com/spring-cloud-samples/fortune-teller

How to push Application sample to PCFdev

    cf cs p-mysql 512mb fortunes-db
    cf create-service -c '{ "git": { "uri": "https://github.com/sergiubodiu/fortune-app-config", "label": "master"  } }' p-config-server standard config-server

Check if the config-server is up

    watch -n 5 cf service config-server

Create Spring Cloud Services

    cf cs p-service-registry standard service-registry
    cf cs p-circuit-breaker-dashboard standard circuit-breaker-dashboard

Verify that this links work

    fortunes.local.pcfdev.io/message
    fortunes.local.pcfdev.io/random
    client.local.pcfdev.io/random