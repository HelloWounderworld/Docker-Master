# Publicando portas de acesso:
- Basicamente, existem inúmeras formas de conseguirmos acessar as portas. Existem formas tbm de acessar uma porta partindo de uma outra porta indo para a porta objetivo, exemplo, para acessar a porta 3000 podemos acessar primeiro a porta 80 e dela acessar a poarta 3000.

- docker run -d -p (número da porta de entrada):(número da porta receptora) --name (nome que vc vai dar ao container) (nome da aplicação):(versão dela) - O -p serve para definirmos de qua porta para qual porta queremos ter o acesso. De forma abreviada, podemos juntar o -d e o -p de forma que fique -dp.

- No nosso caso, rodamos docker run -d -p 80:300 --name BuuDigitalTech app:v2, e note que quando abrirmos o broswer e digitamos apenas "localhost" abrirá a aplicação como queremos. Isso indica que estamos acessando a porta 3000 através da porta 80.

- Como prova disso, ao colocarmos o comando docker ps no terminal aparecerá a seguinte informação sobre o container criado acima

    CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
    101a2c7e215b   app:v2    "docker-entrypoint.s…"   17 minutes ago   Up 17 minutes   0.0.0.0:80->3000/tcp   BuuDigitalTech

    Note que, em PORTS está indicando que qualquer tráfego na porta 80 é direcionado à porta 3000. No caso, indica o redirecionamento de portas.

- Lembrando que se não for feito o redirecionamento da porta como foi feito acima, não será possível rodar o docker em produção! Detalhe importantíssimo!