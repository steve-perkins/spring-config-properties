spring-config-properties
========================
This is one of three Git repositories, which work together to demonstrate using 
[Spring Cloud Config](https://cloud.spring.io/spring-cloud-config/) and [Vault](https://www.vaultproject.io) for 
configuration management:

* https://github.com/steve-perkins/spring-config-properties - Contains:
  * Properties files for global default properties that are available to all applications 
    (i.e. `application.propeties`), 
  * per-application files with properties that are common to that application in every environment 
    (e.g. `sampleapp.properties`), and 
  * environment-specific properties for each application (e.g. `sampleapp-staging.properties`).
* https://github.com/steve-perkins/spring-config-server - An instance of Spring Cloud Config server, configured 
  to serve up *non-secret* properties from the Git repo above, and *secret* properties from Vault.
* https://github.com/steve-perkins/spring-config-sample-app - A sample web application which uses the Spring Cloud 
  Config client to retrieve its config properties from the server above.
  
This demo shows the use case of having two types of config properties:

1. **non-secret** values, which can and should be maintainable by developer teams (e.g. JDBC URL's).
2. **secret** values, which should only be viewable or maintainable by people with specialized access (e.g. 
   usernames and passwords)
   
The non-secret values are stored as-is in the `spring-config-properties` repo.  The *secret* values are manually 
written to Vault.  At runtime, Spring Cloud Config retrieves properties from both sources, giving Vault the higher 
precedence whenever the same property is found in both.

Setup
=====
This repository involves no setup steps.  You don't even have to clone it, as the `spring-config-server` application 
will clone its own copy internally.  Proceed to the steps described in the 
[spring-config-server](https://github.com/steve-perkins/spring-config-server) and 
[spring-config-sample-app](https://github.com/steve-perkins/spring-config-sample-app) project README's.

