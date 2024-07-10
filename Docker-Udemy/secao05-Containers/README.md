# Containers:

## Os containers:
- Baiscamente vamos aprender a utilizar os containers.

## Nomeando containers:
- docker run - é o comando padrão para conseguir fazer algum container rodar.

- Primeiro, antes de prosseguir, tenta deixar o container e as listas de imagens iguais ao que está na aula.

- docker run (nome da aplicação):(versão) - Comando que serve para iniciar alguma aplicação que vc criou. No nosso caso, "docker run app:v2".

- docker run -d (nome da aplicação):(versão) - No caso, o comando anterior vc consegue rodar alguma aplicação, mas vc não iria mais conseguir fazer nada no terminal. Para evitar que isso ocorra e ainda vc consiga rodar a aplicação, bastaria colocar o -d depois do run.

- Note que, ao rodar o comando acima, conseguimos rodar a aplicação, mas o nome do container que estará rodando a aplicação acabará ficando ao cargo da escolha do docker. Entretanto existe sim uma forma de conseguirmos escolher e personalizar para um nome que queremos.

- docker run -d --name (Nome que vc pode dar ao container) (nome da aplicação):(sua versão) - Esse seria a forma em que vc consegue rodar a aplicação de modo que vc mesmo escolha algum nome para o container onde o seu app estará rodando.

- Em boas práticas, é que um container seja iniciado em background!

## Verificando o log de eventos:
- docker logs --help - Mostrará todas as nomenclaturas que podem ser acrescentadas para o docker logs.

- docker logs (options) (container ID)

- docker logs -f (container id) - No caso, ele fica escutando o container, no sentido que qualquer ação que eu fizer dentro do app que está rodando desse container que eu indiquei no log será exibido.

- docker logs -n (algum número inteiro) - Mostrará a lista dos containers de baixo para cima na quantidade em que vc escolhe levando em consideração o id, pode ser a sigla inicial em que um conjunto de id`s tenham, para lista-las.

- docker logs (container id/sigla) - Mostrará todas as lista inteira do docker.

- docker logs -t (container id) - Mostrará o timestamp de quanto tais mensagens de cada logs estão acontecendo.

- Em boas práticas, o desenvolvedor conhece muito bem a importância de usar os logs para debugar e resolver os problemas! Então os estudos de logs pelos terminais de SAAS, no geral, merece uma atenção bem especial para a pessoa aprender bem e evitar dores de cabeças futuras.

## Publicando portas de acesso:
- Basicamente, existem inúmeras formas de conseguirmos acessar as portas. Existem formas tbm de acessar uma porta partindo de uma outra porta indo para a porta objetivo, exemplo, para acessar a porta 3000 podemos acessar primeiro a porta 80 e dela acessar a poarta 3000.

- docker run -d -p (número da porta de entrada):(número da porta receptora) --name (nome que vc vai dar ao container) (nome da aplicação):(versão dela) - O -p serve para definirmos de qua porta para qual porta queremos ter o acesso. De forma abreviada, podemos juntar o -d e o -p de forma que fique -dp.

- No nosso caso, rodamos docker run -d -p 80:300 --name BuuDigitalTech app:v2, e note que quando abrirmos o broswer e digitamos apenas "localhost" abrirá a aplicação como queremos. Isso indica que estamos acessando a porta 3000 através da porta 80.

- Como prova disso, ao colocarmos o comando docker ps no terminal aparecerá a seguinte informação sobre o container criado acima

    CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
    101a2c7e215b   app:v2    "docker-entrypoint.s…"   17 minutes ago   Up 17 minutes   0.0.0.0:80->3000/tcp   BuuDigitalTech

    Note que, em PORTS está indicando que qualquer tráfego na porta 80 é direcionado à porta 3000. No caso, indica o redirecionamento de portas.

- Lembrando que se não for feito o redirecionamento da porta como foi feito acima, não será possível rodar o docker em produção! Detalhe importantíssimo!

## Executando comandos em containers:
- Vamos ensinar uma forma de executar algum comando enquanto o container estiver rodando.

- docker exec (nome do container) ls - Estou executando depois que a imagem está carregado dentro do container. No caso, o comando exibirá todos os arquivos e diretórios disponíveis dentro da imagem que foi criado.

- docker exec (nome do container) (algum outro comando) - De modo geral, esse comando serve dessa forma para podermos verificar/modificar/criar algo dentro do linux sem acessar diretamento o linux.

## Iniciando e parando containers:
- docker stop (nome do container) - serve para parar o container. Importante ressaltar que esse comando não remove o container.

- docker start (nome do container) - serve para rodar novamente o container já existente e que apenas não está rodando.

- Importante ressaltar! para não confundirmos entre docker run, docker stop e docker start, respectivamente, é criar (do zero), parar (sem remover) e iniciar (a partir de uma já existente).

- Se não quiser colocar o nome do container, pode ser o ID.

## Removendo containers:
- docker rm --help - Mostrará as opções para remover.

- docker rm (nome do container) - Serve para remover um container que foi indicado. Lembre-se, com esse comando, não podemos remover o container que esteja em execução.

- docker rm -f (nome do container) - Serve para remover de forma forçada o container que foi indicado.

## Volumes persistentes:
- Vamos deixar claro que quando criamos algum arquivo dentro de uma imagem que esteja rodando dentro de um container e depois que removermos esse container e, em seguida, criarmos novamente a imagem, o arquivo que havíamos criado naquela imagem não estará mais nela.

- Bom, isso é claro de se pensar, pois o tal arquivo que foi criado dentro de uma aplicação rodando, nunca existiu originalmente no projeto em que se cria a imagem pelo Dockerfile.

- Mas existem uma forma de conseguirmos com que os arquivos criados estejam permanecidos mesmo ocorrendo tais processos, que são chamados de volumes persistentes.

- docker volume create (nome do volume) - Serve para criar o volume dentro da aplicação.

- docker volume inspect (nome do volume) - Serve para inspecionar como está a estrutura do volume.

- docker run -d -p (número da porta de partida):(número da porta de chegada) --name (nome que será dado ao container) -v (nome do volume):/(nome do app onde vc quer add o volume) (nome do app):(versão dela) - No caso, ele serve para vc conseguir criar um container novo e criar algum volume em alguma pasta especificando o caminho dela. Um exemplo disso seria, docker run -d -p 3000:3000 --name kiwi -v app-dados:/app/dados app:v2.

- docker exec -it (nome do container) sh - executa algum container de forma interativa.

- docker rm -f (nome do container) - Remoção forçada.

- Nome que, ao removermos o container acima a pargunta que podemos fazer seria, e a pasta dados e o arquivo docker.txt que criamos dentro do modo interativo? Foi excluído? A resposta é não. O fato de eu ter criado a pasta dados pelo volume, quando criarmos um outro container de nome diferente com o mesmo docker run que rodamos para criar o container kiwi, executado isso no modo interativo irá aparecer as pastas que foi criado pelo volume.

- No caso, para boas práticas, sempre que for criar alguma pasta ou arquivo novo, vamos criar pelo volume e não diretamente dentro do container.

## Copiando arquivos de host para o container:
- Vamos aprender a copiar arquivos ou pasta que estão dentro de um container em execução de modo interativo para dentro de um container.

- docker exec -it (nome do contianer) sh - Executando um container no modo interativo.

- docker cp (origem) (destino) - docker cp kiwi2:/app/text.txt ., no caso a origem é kiwi2:/app/text.txt e o destino é no meu local ".".

- Com o mesmo comando acima, podemos criar uma cópia de um arquivo do local para alguma aplicação que roda de forma interativa.

## Passo a passo de como acessar o container remotamente pelo VSCode/Cursor para abrir os seus respectivos codigos fontes:

    https://code.visualstudio.com/docs/devcontainers/attach-container#:~:text=To%20attach%20to%20a%20Docker,you%20want%20to%20connect%20to.