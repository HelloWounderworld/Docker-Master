# Docker Compose:

## O Docker Compose:
- O docker compose ele possibilita rodar vários containers simultaneamente de forma que todas elas estejam relacionados ou não. Isso significa que podemos rodar um container para frontend, outro para backend de forma que uma ação de um outro container afete no outro.

## Instalando o Docker Compose:
- Precisamos verificar se o docker compose já está instalado na sua máquina ou não. Para isso seria necessário verificar pelo google como se instala o docker compose. (https://docker-docs.netlify.app/compose/install/)

- docker-compose --version - Verifica se está ou não instalado o docker compose e a sua versão.

- docker version - serve para ver a versão do docker que vc usa.

## Limpando a maquina local:
- Antes de começarmos a usar o docker compose, precisamos fazer uma limpeza na máquina local para facilitar a execução e o gerenciamento dos multi-containers que vc irá criar através do docker compose. Existem duas formas de realizar a tal limpeza, a forma fácil e a difícil.

- Forma difícil:

    - docker image (ou container) rm (id da imagem ou do container) - Remoção uma por uma.

- Forma fácil:

    - Entra no docker desktop e clica no troubleshoot e em seguida clica no clean/purge data para apagar praticamente todas as imagens e containers que foram criados.

## Download do projeto Netflix:
- Basta realizar o download do arquivo netflix.zip. Mas ela já está salvo no meu drive tbm.

## Rodando o projeto Netflix:
- docker-compose up - Vai ler o arquivo docker-compose e começar a construção do que está sendo pedido dentro desse arquivo.

## A linguagem YAML:
- A linguagem YAML, cujos os arquivos são salvos no formato .yml ou .yaml, definem-se como uma linguagem de data serialization.

- data serialization:

    - Linguagem muito utiliada para escrever códigos e/ou arquivos de configurações.

- A sequência de leitura do arquivo YAML é sempre de cima para baixo. Logo, a ordem em que vc coloca os códigos e/ou configurações para leitura acaba ganhando uma importância.

- YAML tem um processo de organização chamado indentação (indetation), ou seja, por meio do espaçamento dado pelo tab tudo o que digitar a partir desse espaço para baixo pertencerá para a função mãe. Um exemplo, no arquivo docker-composer.yml tem o serives e após ela tem um tab onde tem os frontend e backend, etc... No caso esses pertencem ao service. E fora dela não pertence ao services.

## Criando um docker compose file:
- Vamos aprender a criar um docker-compose do zero! Faremos isso no projeto netflix.

- Passos básicos para construir o arquivo docker-compose.yml:

    - Primeiro: Precisa-se definir uma versão. Para isso é recomendável que procure a versão mais atualizada e possível! Para isso vc pode pesquisar pelo google ou acessar esse link (https://docs.docker.com/compose/compose-file/) e ir no Legacy versions e por lá verificar a versão mais atual. No nosso caso será
    version: "3.8"

    - OBS: Na parte onde está escrito Compose Specification estará todos os parâmetros que vc pode colocar no arquivo docker-compose.yml

    - Segundo: Vamos colocar os tipos de serviços. No caso, os tipos de serviços que selecionamos foram frontend, backend e db

    - Para o frontend precisamos definir o que vai dentro dela. E isso depende muito do que está configurado no Dockerfile do frontend. No caso, existem duas formas de eu conseguir configurar, uma é ir vendo um por um o que está escrito no Dockerfile e outra, mais fácil, é especificar dentro do frontend dizendo para ler o Dockerfile que está dentro do frontend. Em seguida, precisamos definir a porta dentro dela tbm. O que falta colocar são as dependências. No caso, o frontend ele depende do backend, assim como backend depende do db. É necessário especificar isso para evitar que ocorra futuros problemas.

    - Para o backend é a mesma analogia para construção acima. Além disso, no backend precisa-se conectar com o banco de dados, então precisamos colocar essa condição relacional que é o enviroment e o comand.

    - Para o db, vamos construir uma imagem de um banco de dados mesmo. No caso, vamos usar o do mongoDB. A imagem do qual mongodb vamos usar podemos encontrar a sua extensão no dockerhub, no nosso caso vamos usar o mongo:4.0-xenial. E a porta para esse banco de dados podemos pesquisar no google jogando mongodb ports (o mesmo pode ser feito para outros bancos de dados). Vamos precisar definir um volume dentro db tbm.

    - Terceiro: Vamos definir o volume para a aplição vidly.

## Rodando e parando o docker compose:
- docker-compose --help - Mostra todos as opções que precisamos para esse comando.

- docker-compose up --build - serve para construir e iniciar.

- docker-compose up -d - serve para vc conseguir iniciar e depois que iniciar ainda ficar livre para mexer no terminal

- docker-compose ps - lista todas as aplicações que estão rodando

- docker-compose down - serve para parar de rodar as aplicações seus.

## A rede do Docker:
- Vamos verificar mais a fundo de como os serviços que colocamos no docker-compose se conversam. No caso, eles se conversam por redes endereçado pelo IP. Ou seja, o frontend tem um IP, o backend tem um IP e o db tem um IP, e as comunicações desse IP para outro IP que é o que possibilita a comunicação entre front, back e db, por baixo dos panos.

- docker-compose up -d - Subiremos a aplicação.

- docker exec -it -u root (id do container) sh - vamos executar o frontend de forma interativa. 

- Em seguida, no modo interativo, colocamos o comando ifconfig e é dela que podemos ver o IP do frontend.

- Em seguida podemos colocar o comando ping backend para saber o IP do backend. Analogamente, podemos fazer para o db.

## Da mesma forma que executamos o frontend de forma interativa, podemos fazer para o backend tbm.
- Docker Compose logs:

    - docker-compose logs - mostrará todas as atividades realizadas das aplicações que foram criadas e que estão rodando pelo docker-compose.yml.
    
    - docker-compose logs --help - mostrará todos os parâmetros que vc pode implementar junto com esse comando.