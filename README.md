# Como utilizar #

Dependências:

  * Docker engine v1.13 ou superior. Seu pacote fornecido pelo sistema operacional pode ser um pouco antigo, se você encontrar problemas, faça upgrade. Veja [https://docs.docker.com/engine/installation](https://docs.docker.com/engine/installation)
  * Docker compose v1.12 ou superior. Veja [docs.docker.com/compose/install](https://docs.docker.com/compose/install/)

Após o processo citado, simplesmente acesse o seu projeto e execute `docker-compose up -d`. Isso irá executar todos os contêineres e deixarão os mesmos executando em segundo plano.

## Serviços expostos fora do seu ambiente ##

Você pode acessar sua aplicação via **`localhost`** ou com o **`ip`** da sua máquina virtual.

Serviço | Endereço fora dos contêineres
------|---------
Webserver | [localhost:8080](http://localhost:8080)
MySQL | **host:** `localhost`; **port:** `8082`

## Hosts dentro do seu ambiente ##

Configure sua aplicação para utilizar os serviços habilitados:

Serviço | Hostname | Porta
------|---------|-----------
php-fpm | php-fpm | 9000
MySQL | mysql | 3306 (default)
Redis | redis | 6379 (default)

# Docker compose #

Acesse a pasta onde se encontra o seu docker-compose.yml:

  * INICIAR os contêineres em segundo plano: `docker-compose up -d`
  * INICIAR os contêineres em primeiro plano: `docker-compose up`.
  * PARAR os contêineres: `docker-compose stop`
  * EXCLUIR os contêineres: `docker-compose kill`
  * VISUALIZAR os logs dos contêineres: `docker-compose logs`
  * ACESSAR os contêineres: `docker-compose exec SERVICE_NAME COMMAND` onde o `COMMAND` é o que você queira executar.

Exemplos:

   * Shell do container PHP, `docker-compose exec php-fpm bash`
   * Execute o console symfony, `docker-compose exec php-fpm bin/console`
   * Abra o shell do MySQL, `docker-compose exec mysql mysql -uroot -pCHOSEN_ROOT_PASSWORD`