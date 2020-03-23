# Ambiente Traefik com Let's Encrypt na AWS EC2


## Requisitos

* Domínio (recomendo o `.me`, sai bem em conta!)
* Certificado https validado pelo Let's Encrypt
* Instância na EC2 (pode ser uma t2.micro, usando o free tier)
* [opcional] Uma zona hospedada no Route53 (pode fazer essa gestão no seu provedor de nome do domínio também!)


## Configuração do domínio


## Configuração da instância EC2
* Instalar docker
* Instalar docker-compose
* Instalar htpasswd (para gerar a senha encriptada para a dashboard do traefik)


## Configuração do Traefik
* No arquivo `traefik.toml`, fazer as seguintes alterações:
  - Na linha `email = ""`-> adicionar o email usado para a criação do certificado com o let's encrypt
  - Na linha `domain = ""`-> adicionar o seu domínio
  - Na linha `users = [""]`-> adicionar o usuário e senha gerado pelo htpasswd
* No arquivo `docker-compose.yml`, fazer as seguintes alterações:
  - Na linha ` - traefik.frontend.rule=Host:` -> adicionar o domínio ou subdomínio onde o dashboard do traefik vai ser visualizada
  
## TODO
 - [ ] Adicionar configuração da EC2 usando Ansible
 - [ ] Adicionar renew automático do certificado
