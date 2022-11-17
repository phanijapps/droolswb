Step 1 : Copy business central war and keycloak adapter to deployment dirctory

https://github.com/keycloak/keycloak/releases/download/20.0.1/keycloak-oidc-wildfly-adapter-20.0.1.zip

https://download.jboss.org/drools/release/7.73.0.Final/business-central-7.73.0.Final-wildfly23.war


Step 2: 
Run the following command

docker build --pull --rm -f "Dockerfile.drools" -t droolswb:latest "." 


Step 3 :

docker-compose -f docker-compose.yaml up


Step 4: Configure Key cloak and update the standalone.xml

<secure-deployment name="business-central.war">
<realm>dempo</realm>
<realm-public-key>MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvOHVvlKXXN/a1g7gO7ixtgSoxdskpPLaTG6Xh4EC1xb8UqleAoyZ1goB/GzfQBkfQtc9FJYk4RCsflWm2tO5rnPiM2dSuXWl03FA+OEiiORLxDhLwGbYtYETCQpYwlb5et7UyqwmlNGaSZT6AGeXwfhweqSLp9oXkJs/Hvn7Vdi75jDsTE7Jhi/r8NsuWL7dvdb8pPG699nJmaiLrnIxdzpthW/y7fYPNfmJDb/sKljt8xywvM5j0EQj4TEBIPHqyMO2oRx7QQfOOlAW25TCM+2gyVltgd8vI/mOgiXjGVCxtBs5Bfs3I9Vkx9LZ9ZiXRwrNyOC1BsLcaGGVxyzKDQIDAQAB</realm-public-key>
<auth-server-url>http://keycloak:8180</auth-server-url>
<ssl-required>external</ssl-required>
<resource>kie</resource>
<enable-basic-auth>true</enable-basic-auth>
<credential name="secret">ryEEQ00H7XuMHfCFktPqeC9vhBLWnijW</credential>
<principal-attribute>preferred_username</principal-attribute>
</secure-deployment>