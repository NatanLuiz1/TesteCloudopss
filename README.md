# TesteCloudopss
Criação de conteiners e imagens com Docker e Jenkins

   Requisitos para rodar a aplicação
   
- Python:3
- Docker
- Jenkins

   Instruções da utlização da aplicação
- Clone este repositório para um repositorio local a sua escolha;
- Após isso execute o "CMD" ou "SHELL" e vá até o local onde escolheu clonar o seu repositório;

- Logo execute o seguinte comando para inicializar os conteiners:
 
  docker-compose up -d

- Após isso ainda no "CMD" entre na pasta jenkins e digite o mesmo comando "docker-compose up -d" para inicializar o jenkins que está configurado para a porta 8084;

- Acesse seu Browser e acesse a pagina "localhost:8084" faça o login com login: admin senha: admin;

- Logo após selecione o job "testeflask-api" e realize o build now para teste;
