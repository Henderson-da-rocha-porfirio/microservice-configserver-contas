# contas
## Configurar no application.properties(nome, profile:
````
spring.application.name=contasconfigserver
spring.profiles.active=prod
spring.config.import=optional:configserver:http://localhost:8071/

management.endpoints.web.exposure.include=*
````
## Criar uma classe ContasServiceConfig, com as devidas anotações, para buscar o nome, o prefixo(prefixos que ficam nas properties da pasta config, ex: accounts, cards e etc) e o profile do microserviço:
````
@Configuration
@ConfigurationProperties(prefix = "accountsconfigserver")
````
## Prestar a atenção para que a leitura do config server(vide classe AccountsServiceConfig) funcione:
> a. Olhar os nomes das properties, se estão no mesmo nome da aplicação.

> b. Verificar os prefixos que estão dentro das properties. Ex: accounts.algumacoisa

> c. Não se preocupar com o "-" de build-version. A Spring o transforma.

> d. Não se preocupar com os sufixos: hostname e etc. Os valores são mapeados assim mesmo.

> e. A lista de arrays deve ter o mesmo nome que foi colocado na properties correspondente.

## Criar a model properties

## Testando no Postman:
````
http://localhost:8080/account/properties
````
### Resposta:
````
{
    "msg": "Bem vindos(as) ao Tuyo Accounts Prod application",
    "buildVersion": "1",
    "mailDetails": {
        "hostName": "prod-accountsconfigserver@tuyosistema.com",
        "port": "9010",
        "from": "prod-accountsconfigserver@tuyosistema.com",
        "subject": "Detalhes da Conta de Tuyo Bank Prod Environment"
    },
    "activeBranches": [
        "Hyderabad",
        "Paris",
        "NewYork"
    ]
}
````
