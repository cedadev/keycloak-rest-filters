# Keycloak REST Filters

Some helpful REST Resource providers for Keycloak.

You can deploy this as a module by running:

```bash
$KEYCLOAK_HOME/bin/jboss-cli.sh --command="module add --name=uk.ac.ceda.keycloak-rest-filters --resources=target/keycloak-rest-filters.jar --dependencies=org.keycloak.keycloak-core,org.keycloak.keycloak-server-spi,org.keycloak.keycloak-server-spi-private,javax.ws.rs.api"
```

Then registering the provider by editing `standalone/configuration/standalone.xml` of your Keycloak installation and adding the module to the providers element:

```xml
<providers>
    ...
    <provider>module:uk.ac.ceda.keycloak-rest-filters</provider>
</providers>
```

Then start the Keycloak server. Assuming a default configuration, you can reach the API from `http://localhost:8080/auth/realms/{realm}/filter` (`realm` will typically be "master").

## Search by attribute

Use the `/filter/attribute` endpoint to search for users by attribute value:

```/filter/attribute/{name}/{value}```
