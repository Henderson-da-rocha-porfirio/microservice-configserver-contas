# @RefreshScope
> a. Invoca o reload às propriedades(properties) que mudaram sem a necessidade de reiniciar o microserviço.
> 
> b. E é preciso inserir também em application.properties:
````
management.endpoints.web.exposure.include=*
````