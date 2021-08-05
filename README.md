# Keycloak REST Search

Some helpful REST Resource providers for searching Keycloak.

You can deploy this as a module by running:

```bash
$KEYCLOAK_HOME/bin/jboss-cli.sh --command="module add --name=uk.ac.ceda.keycloak-rest-search --resources=target/keycloak-rest-search.jar --dependencies=org.keycloak.keycloak-core,org.keycloak.keycloak-server-spi,org.keycloak.keycloak-server-spi-private,javax.ws.rs.api"
```

Then registering the provider by editing `standalone/configuration/standalone.xml` of your Keycloak installation and adding the module to the providers element:

```xml
<providers>
    ...
    <provider>module:uk.ac.ceda.keycloak-rest-search</provider>
</providers>
```

Then start the Keycloak server. Assuming a default configuration, you can reach the user search API from `http://localhost:8080/auth/realms/{realm}/user-search` (`realm` will typically be "master").

## Search for users by attribute

Use the `/user-search/attribute` endpoint to search for users by attribute value:

```/user-search/attribute/{name}/{value}```
