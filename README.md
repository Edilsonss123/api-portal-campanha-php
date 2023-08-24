<!-- GETTING STARTED -->
## Començando

Este é um exemplo de como você pode dar instruções sobre como configurar seu projeto localmente. 
Para colocar uma cópia local em funcionamento, siga estas etapas de exemplo simples. 

### Pré-requisitos

This is an example of how to list things you need to use the software and how to install them.
* docker
  ```sh
  docker --version
  ```
  - Se não possuir o docker instalado siga a documentação do [https://docs.docker.com/get-docker/][Docker]
  - após instalação do docker passe para o póoximo passo.

### Instalação

1. Acessando no terminal faça o clone do repositório
   ```sh
   git clone https://github.com/Edilsonss123/api-crud-php
   ```
2. Renomeie o arquivo api/.env.example para .env
3. Edite o arquivo .env adicione uma valor para a variável ```JWT_CHAVE``` que será utilizada para geração do token JWT
4. Com o terminal de comandos navegue até o diretorio do arquivo docker-composer.yml e execute o comando abaixo, a primeira vez vai demorar uma pouco
pois o docker vai fazer a montagem do container necessário para rodar a aplicação.
   ```sh
   docker-compose up --build -d
   ```
6. Ao finalizar será lançando no terminal a mensagem abaixo
   ```sh
      Creating mysql-portal-campanha ... done
      Creating crud-portal-campanha  ... done
   ```
7. Para acessar o container execute
   ```sh
      docker exec -it crud-portal-campanha /bin/bash
   ```
8. Dentro do container acesse o diretorio ```cd /var/www/html/``` nesse momento vamos criar as tabelas e popular o banco de dados
    - criar as tabelas execute  
     ```sh
          sh php database/migrations/criando_tabela_campanha_e_usuario_e_arquivos_campanha.php
     ```
    - popular as tabelas execute 
     ```sh
          sh php database/seed/campanhasSeed.php &&  php database/seed/usuariosSeed.php
     ```

9. Para habilitar o roteamento da aplicação vamos utilizar o server do php apontando para o arquivo de configuração 
   ```sh php -S 0.0.0.0:5020 index.php```
10. No final desse passo a passo a aplicação estará disponivel para ser acessada no navegador na porta 5020

<p align="right">(<a href="#readme-top">back to top</a>)</p>



## Consumindo API
Para facilitar o teste utilize a collection do postman [https://documenter.getpostman.com/view/5807678/2s9Y5Wx3rh](https://documenter.getpostman.com/view/5807678/2s9Y5Wx3rh)


## Bibliotecas utilizadas

Foram utilizadas as bibliotecas abaixo para contrução da API: 
1. ```illuminate/database``` -> orquestração com o banco de dados
2. ```izniburak/router``` -> roterização da API
3. ```rakit/validation``` -> validação dos dados informados nas requests
4. ```vlucas/phpdotenv``` -> configuração das variaveis de ambiente
5. ```firebase/php-jwt``` -> autenticação JWT
6. ```php-di/php-di``` -> realização da injeção de dependencia

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

