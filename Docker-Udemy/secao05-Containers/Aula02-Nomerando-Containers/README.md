# Nomeando containers:
- docker run - é o comando padrão para conseguir fazer algum container rodar.

- Primeiro, antes de prosseguir, tenta deixar o container e as listas de imagens iguais ao que está na aula.

- docker run (nome da aplicação):(versão) - Comando que serve para iniciar alguma aplicação que vc criou. No nosso caso, "docker run app:v2".

- docker run -d (nome da aplicação):(versão) - No caso, o comando anterior vc consegue rodar alguma aplicação, mas vc não iria mais conseguir fazer nada no terminal. Para evitar que isso ocorra e ainda vc consiga rodar a aplicação, bastaria colocar o -d depois do run.

- Note que, ao rodar o comando acima, conseguimos rodar a aplicação, mas o nome do container que estará rodando a aplicação acabará ficando ao cargo da escolha do docker. Entretanto existe sim uma forma de conseguirmos escolher e personalizar para um nome que queremos.

- docker run -d --name (Nome que vc pode dar ao container) (nome da aplicação):(sua versão) - Esse seria a forma em que vc consegue rodar a aplicação de modo que vc mesmo escolha algum nome para o container onde o seu app estará rodando.

- Em boas práticas, é que um container seja iniciado em background!