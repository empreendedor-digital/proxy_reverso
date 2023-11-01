# Proxy_reverso

Repositório com exemplos de configurações de proxy reverso para auxiliar em problemas de compatibilidade com HTTPS.

**Considerações:**

- o proxy reverso vai disponibilizar a conexão local via HTTP na porta 8080;
- substituir "endereco.local" pelo ip ou fqdn interno;
- substituir "endereco.publico" pelo ip ou fqdn público de destino;
- a url tem que ser alterada na aplicação para passar pelo proxy. 

```
 - url original: https://endereco.publico/teste/servico?wsdl
 
 - url passando pelo proxy: http://endereco.local:8080/teste/servico?wsdl
```

**Requisitos:**

- [Caddy](https://caddyserver.com/) ou [Docker](https://docker.com/) / [Podman](https://podman.io/) 


Caddy:
```
caddy reverse-proxy --from http://endereco.local:8080 --to https://endereco.publico --change-host-header
```

Docker:
```
docker run -d -p 8080:80 -it docker.io/caddy caddy reverse-proxy --from http://endereco.local --to https://endereco.publico --change-host-header
```

Podman: 
```
podman run -d -p 8080:80 -it docker.io/caddy caddy reverse-proxy --from http://endereco.local --to https://endereco.publico --change-host-header
```
