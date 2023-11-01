# Proxy_reverso

Repositório com exemplos de configurações de proxy reverso para auxiliar em problemas de compatibilidade HTTPS.

**Considerações:**

- o proxy reverso vai disponibilizar a conexão local via HTTP na porta 8080;
- substituir "endereco.local" pelo ip ou fqdn interno;
- substituir "endereco.publico" pelo ip ou fqdn público de destino;



**Requisitos:**

- [Docker](https://docker.com/) / [Podman](https://podman.io/)


Exemplo utilizando [Caddy](https://caddyserver.com/):

Docker:
```
docker run -p 8080:80 -it docker.io/caddy caddy reverse-proxy --from http://endereco.local --to https://endereco.publico --change-host-header
```

Podman: 
```
podman run -d -p 8080:80 -it docker.io/caddy caddy reverse-proxy --from http://endereco.local --to https://endereco.publico --change-host-header
```
