# Criando Imagens Docker:

## O que são Imagens e Containers?:

### O que é Imagem:
- Cut-Down OS, ou seja, tem um Sistema Opperacional dentro dele

- Tem todas as bibliotecas que precisa para que a sua aplicação rode

- Tudo que a sua aplicação precisa para funcionar de arquivos estão lá dentro

- Variáveis de ambiente (enviroment variables)

- Basicamente, a definição de uma imagem em Docker seria algo que contém tudo o que vc precisa para uma aplicação funcionar

Uma imagem Docker é um modelo de sistema de arquivos read-only que contém tudo o que é necessário para executar um determinado aplicativo ou serviço. Ela inclui o código do aplicativo, as bibliotecas, as dependências, as configurações e outros artefatos necessários.

As imagens Docker são construídas a partir de instruções definidas em um arquivo chamado Dockerfile. Esse arquivo contém uma série de comandos que descrevem como a imagem deve ser construída. Alguns comandos comuns em um Dockerfile são:

- FROM: Especifica a imagem base a ser usada.

- COPY: Copia arquivos ou diretórios do host para a imagem.

- RUN: Executa comandos durante a construção da imagem.

- CMD: Define o comando padrão a ser executado quando o contêiner é iniciado.

- EXPOSE: Informa quais portas o contêiner irá escutar.

Para configurar as imagens Docker de forma eficiente, siga estas boas práticas:

1. Escolha uma imagem base apropriada: Selecione uma imagem base que seja otimizada para o seu caso de uso, evitando instalar pacotes desnecessários.

2. Crie camadas lógicas: Organize o Dockerfile em camadas lógicas, com cada camada realizando uma tarefa específica. Isso permite reutilizar camadas existentes durante a construção, melhorando a eficiência.

3. Minimize o número de camadas: Cada instrução no Dockerfile cria uma nova camada na imagem. Quanto menos camadas, melhor, pois isso reduz o tamanho da imagem e acelera o processo de construção.

4. Otimize o cache do Docker: O Docker usa um mecanismo de cache para acelerar a construção de imagens. Organize o Dockerfile de modo que as instruções menos propensas a mudanças apareçam primeiro, para aproveitar melhor o cache.

5. Utilize multi-stage builds: Essa técnica permite criar imagens menores e mais otimizadas, separando a construção da aplicação da criação da imagem final.

6. Aplique a melhor compressão: Ao gerar a imagem final, utilize o formato de compressão mais apropriado, como gzip ou zstd, para reduzir o tamanho da imagem.

Seguindo essas boas práticas, você pode criar imagens Docker eficientes, minimizando o tamanho e o tempo de construção, o que facilita o gerenciamento e a distribuição dos seus aplicativos.

Espero que essas informações tenham sido úteis! Sinta-se à vontade para fazer mais perguntas.

Voce pode baixar as imagens bases que seja adequado para configurar a sua imagem oelo seguinte link

    https://hub.docker.com/search

### O que é Container:
- É como se fosse uma VM de forma isolado

- Ele tem start/stop

- É um processo que roda dentro de uma máquina

## A aplicacao:
- Vamos realizar uma aplicação local iniciando tudo do zero pegando um app teste e a partir dela realizar o processo de criação da imagem e, por fim, rodar ela.

    - No Google, procure por Docker Sample Application - https://docs.docker.com/get-started/02_our_app/

    - No link acima, podemos realizar um download de um arquivo zipado para conseguir baixar o arquivo teste que consta com nome getting-started-master e dentro dela pegar apenas o diretório app.

## Instruções do Dockerfile:
- Precisaremos criar um dockerfile dentro do diretório app.

    - FROM - Esse from indica qual imagem irá carregar, um windows, linux ubuntu, center OS, Alpine, etc... E qual que é a plataforma nodejs, python, etc...

    - WORKDIR (Working Directory) - Define em qual diretório quer que a sua aplicação rode sempre

    - COPY/ADD - Esses dois servem para copiar/adicionar todos os arquivos que fazem parte da sua aplicação dentro da sua imagem

    - RUN - diz para rodar tal processo

    - ENV (Enviroment) - Configuração do ambiente, no caso, o que eu preciso dentro do meu linux para rodar a tal aplicação.

    - EXPOSE - é o que é responsável colocar em qual porta local que vc escolheu para rodar a sua aplicação

    - USER - Define o usuário que pode rodar essa aplicação. O uso desse recurso é opcional.

    - CMD/ENTRYPOINT - Servem para vc poder rodar outros comandos que vc deseja implementar no processo de criação da imagem.

#### OBS: Uma boa pratica de configurar um Dockerfile seria em utilizar, somente um FROM dentro dela!!!
Sim, é considerada uma boa prática utilizar apenas um comando FROM no início do Dockerfile. Essa abordagem é recomendada pelos guias oficiais de boas práticas para construção de imagens Docker.

Algumas razões pelas quais é preferível usar apenas um FROM no início do Dockerfile:

Simplicidade e Legibilidade: Ter apenas um comando FROM torna o Dockerfile mais simples e fácil de entender. Isso facilita a manutenção e a colaboração entre equipes.

Desempenho: Usar múltiplos comandos FROM pode aumentar o tempo de construção da imagem, pois cada etapa de FROM inicia uma nova camada no sistema de arquivos da imagem. Quanto menos camadas, mais rápida será a construção.

Rastreabilidade: Com apenas um FROM, fica mais fácil rastrear a origem da imagem base e entender a proveniência da imagem final.

Segurança: Usando apenas uma imagem base, é possível garantir que todas as atualizações de segurança e correções sejam aplicadas de forma consistente em toda a imagem.

Organização: Ao invés de ter múltiplas etapas de FROM, é preferível criar imagens intermediárias ou usar recursos como estágios de compilação (multi-stage builds) para separar diferentes fases da construção da imagem.

Embora existam casos específicos em que o uso de múltiplos comandos FROM pode ser justificado, a recomendação geral é seguir a abordagem de um único FROM no início do Dockerfile. Isso ajuda a manter a imagem Docker mais limpa, eficiente e fácil de entender e manter.

Há alguns casos em que pode ser adequado utilizar múltiplos comandos FROM dentro de um Dockerfile. Aqui estão alguns exemplos:

Multi-stage Builds: Essa é a principal razão para usar múltiplos FROM em um Dockerfile. A técnica de multi-stage builds permite separar o processo de construção em etapas independentes, usando diferentes imagens base. Isso é útil quando você precisa construir uma aplicação a partir de uma imagem maior e, em seguida, copiar apenas os artefatos necessários para uma imagem final menor e mais leve.

Construção de Aplicações Multilinguagem: Quando você precisa construir uma aplicação que envolve diferentes linguagens de programação (por exemplo, um backend em Python e um frontend em Node.js), usar múltiplos FROM pode ajudar a isolar e organizar melhor as etapas de construção.

Reutilização de Imagens Intermediárias: Em casos em que você precisa construir imagens complexas com muitas dependências, pode ser benéfico criar imagens intermediárias que possam ser reutilizadas em outros Dockerfiles. Isso ajuda a reduzir o tempo de construção e o tamanho da imagem final.

Testes e Validação: Você pode usar múltiplos FROM para criar etapas de teste e validação separadas da construção final da imagem. Isso facilita o processo de depuração e garantia de qualidade.

Imagens Customizadas: Algumas vezes, você pode precisar estender ou personalizar uma imagem base existente. Nesse caso, usar um segundo FROM pode ser uma abordagem adequada.

É importante notar que, mesmo quando múltiplos FROM são usados, é recomendado manter o Dockerfile o mais simples e legível possível. Evite abusar dessa prática, pois ela pode tornar o Dockerfile mais complexo e dificultar a manutenção.

Em resumo, o uso de múltiplos FROM é justificado principalmente em cenários de construção de aplicações complexas, onde a separação de etapas traz benefícios significativos em termos de desempenho, organização e manutenibilidade.

## Escolhendo a imagem:
- A aplicação teste que baixamos do site da Docker, conseguimos verificar em que tipo de versões que o app está configurado para podermos instruir a construção Dockefile

- Configurado o Dockerfile no diretório app de acordo com a instrução (Neste caso só foi colocado FROM node:12-alpine), então bastaria rodar no terminal o comando docker build -t app .

- O comando acima serve para construir uma imagem

- Rodando o comando docker run -it app sh, ela irá rodar essa imagem de forma interativa e dentro dela poderemos verificar que tipo de versão do node estará presente dentro dela

- Para sair do modo interativo acima, bastaria digitar Ctrl/Command + c ou exit

## Copiando arquivos na imagem:
- Podemos colocar dentro do Dockerfile o COPY da forma (COPY yarn.lock, ou se quiser colocar mais conteúdo, COPY yarn.lock package.json)

- Uma segunda forma de uso é quando vc queira copiar um arquivo para dentro de um outro diretório, no caso, a estrutura exemplo seria COPY package.json /app (se for simples arquivo) ou COPY package.json /app/ (se for dois arquivos)

- Se quiser copiar todos os arquivos json dentro de um diretório, seria COPY *.json /app/

- Se quiser copiar todos os arquivos, seria COPY . /app/

- Se quiser definir que toda a execução ocorre somente dentro de um diretório, em vez de ficar especificando pelo COPY para qual diretório, antes disso bastaria colocar o WORKDIR /app, para especificar que tudo ocorrerá dentro do diretório app.

- A diferença entre COPY e o ADD está no fato de que se vc quiser realizar alguma implementação que esteja em algum web site, em vez do COPY, vc utilizará o ADD.

- No caso, se for uma cópia simples, usamos o COPY, mas se for uma cópia de um website ou arquivo zip, usamos o ADD.

- Implementado o WORKDIR e COPY no Dockerfile dentro do diretório app, bastaria rodar pelo terminal o mesmo comando para construir a imagem, mas desta vez com os WORKDIR e COPY implementados

- Desta vez, se rodarmos de forma interativa como foi feito antes, poderemos ver que a ação do COPY estará implementado de forma que vc colocando o comando ls, irá aparecer todos os arquivos que tem no diretório app copiados dentro da pasta interativa.

## Utilizando o RUN:
- No caso, visto que quando rodamos a imagem app que criamos de forma interativa, nela não consta o python rodando. Para isso, usamos o RUN para conseguirmos instalar o python ao criar, novamente, a mesma imagem, só que desta vez com o python instalado.

- Cada vez que colocamos mais dependências pelo Dockerfile, conseguimos ver que a imagem criada vai aumentando de tamanho.

## Configurando Variáveis:
- Agora, vamos como se usa o ENV, no caso, ela serve para quando queremos dizer em qual ambiente queremos que ela rode, como API. A forma como se implementa seria API_URL="o link url".

## Utilizando o EXPOSE:
- O EXPOSE serve para conseguir definir qual porta para o localhost em que o container irá rodar. (Para a implementação que fizemos foi o EXPOSE 3000)

- Um detalhe muito importante. Quando acessamos o container localmente especificando uma porta, a especificação, somente, serve para dizer à máquina na qual estou rodando o container qual porta eu quero abrir para utilizar. Isso significa que não irei poder utilizar o ifconfig e acessar o mesmo app pelo outro aparelho mesmo que eu tenha o ip da máquina onde o container esta rodando.

## Utilizando o CMD:
- No caso, iremos especificar ao CMD qual o arquivo que queremos que rode. (CMD ["node", "src/index.js"])

- A diferença entre o RUN e o CMD está no fato de que o RUN roda durante a construção da imagem. Já o CMD tem como funcionalidade somente depois que a imagem está criada, para inicialização da imagem ou durante em que a imagem esteja rodando.

- Note que o yarn, tbm, faz parte do programa app que estamos rodando, então precisamos rodar ela tbm de modo que ela faça parte da composição de uma imagem. Para isso, bastaria acrescentar RUN yarn install --production

## Adicionando um usuário na imagem:
- RUN addgroup dev && adduser -S -G leonardo dev

- USER leonardo

- Colocamos o comando acima depois que o WORKDIR para conseguimos rodar os usuários que estão dentro do container que foi criado.

- Por hora não vamos precisar desses comandos acima para a finalidade de teste do app.

## Rodando a sua aplicação:
- Primeiro constroi a imagem, caso tenha add mais dependências no Dockerfile

- Em seguida coloque docker run -dp 3000:3000 app

- Em seguida abra um navegador no Broswer e coloque localhost:3000

- Ao verificar no Docker Desktop estará indicando que ela está rodando na porta 3000

## Melhorando a performance:
- Cada vez mais que add as dependências a imagem fica cada vez mais pesado para rodar ela ou até mesmo na sua criação. Existe uma maneira de deixar o processamento dessa imagem mais leve usando o cache.

- O formato como vc colocar o COPY no Dockerfile, ele pode melhorar a performance do processamento. No caso, colocando, por exemplo, o COPY package.json antes e depois o COPY . ., melhoramos a performance da construção da imagem, pois estamos verificando primeiro se o arquivo núcleo onde há todas as dependências houve ou não alguma alteração e se não tiver, então bastaria colocar da mesma forma como estava antes sem precisar passar novamente pelo processo de recriamento. Ou seja, estará tudo cacheado.

- No caso, ao acrescentarmos o arquivo README.txt, como não houve nenhuma alteração no package.json e o COPY package.json irá confirmar isso, então não será necessário rodar os dois RUNS que estão sendo pedidos para processar.

- Logo, em Dockerfile, podemos tornar melhor a performance do processamento só pela alteração da ordem que colocamos os comandos ou a forma como pedimos para que a imagem seja construída.

## Adicionando tags a imagens:
- as tags servem para que possamos realizar as identificações das imagens. Muitas vezes quando temos versões diferentes de imagens com mesmos nomes.

- digitando docker imagens e podemos visualizar na parte escrito TAG onde será listado.

- No caso, podemos ver que ao longo da aula realizamos várias builds de imagens com o mesmo nome app. Sendo que a cada build as suas versões eram diferentes. Entretanto, como estava sendo construída sobre a mesma imagem, então o que ocorria era uma sobrescrição da nova versão sobra a versão velha no processo de build

- Para evitar que isso ocorra que existe as tags que podemos separar as mesmas imagens com versões diferentes.

- docker build -t app:v1.0.0 .

- Note que, ao rodar o comando acima, podemos verificar, docker images, que foi criado uma imagem app mas com a tag v1.0.0

- docker imagem remove app:v1.0.0 - Serve para remover a imagem app com a tag v1.0.0

- docker image tag app:latest app:v1.0.0 - Serve para trocar a tag latest da imagem app para a tag v1.0.0

- para alterar a tag de outras imagens funciona de forma análoga. Se bem que, em vez de alterar é como se criasse um clone seu mas com o outro nome.

- Agora, vamos aproveitar essa nova imagem da versão v1.0.0 com uma outra nova versão.

- docker build -t app:v1.0.1 .

- Literalmente, agora sabemos qual a imagem mais atualizada.

- Note que, a cada build da imagem, sempre ela aparece como uma tag latest que é algo perigoso como no nosso caso, pois a versão mais atualizada é o v1.0.1

- Por isso, é recomendável que sempre que forem buildar alguma imagem que coloque a tag especificando diretinho a versão dela para melhor o controle e geranciamento.

## Compatilhando imagens:
- Usaremos o docker hub, assim como é usado no github para vc conseguir compartilhar os seus arquivos e suas produções.

- No caso, com usuário logado clique em Create Repository

- Agora, usando o terminal, vamos subir alguma imagem para o docker hub.

- docker build -t app:v1 .

- Com o comando acima, vamos criar primero uma versão

- Vamos agora add uma nova tag igual ao repositório que foi criado no docker hub (hellowounderworld/app)

- docker image tag (image ID) hellowounderworld/app:v1

- Agora, vamos fazer um upload do que criamos acima.

- Primeiro, pelo terminal, vamos logar no docker hub

- docker login

- docker push hellowounderworld/app:v1 

- O comando acima serve para enviar toda a imagem para o docker hub

- Feito isso, ao acessar o docker hub com o seu usuário logado, poderá ver que no repositório que vc criou haverá a imagem com a versão que vc criou.

- A cada versão atualizada, fazemos os mesmos processos de push para conseguirmos compartilhar as nossas imagens.

## Salvando e carregando imagens:
- Podemo transferir sempre as imagens de uma máquina para outra por intermédio do docker hub, o que é recomendável. Mas existem formas mais diretas de realizar isso.

- docker image save --help

- Mostrará as opções para salvar

- docker image save -o appv2.tar app:v2

- Ao olhar na pasta/diretório app podemos ver o arquivo appv2.tar que é o arquivo comprimido onde foi salvo a imagem app v2

- docker image rm app:v2

- docker image rm (Image ID siglas iniciais)

- docker image load --help

- docker image load -i appv2.tar

## Construindo a minha primeira imagem passo a passo:

### Ponto de partida - FROM:
A primeira linha FROM ubuntu:22.04 é uma instrução muito importante em um Dockerfile, pois ela define a imagem base a partir da qual sua imagem será construída.

    FROM ubuntu:22.04

Neste caso, a imagem base é o Ubuntu na versão 22.04 LTS (Long Term Support). Isso significa que sua imagem Docker terá como ponto de partida a distribuição Ubuntu 22.04.

### Instrucao SHELL
Já a segunda linha SHELL ["/bin/bash", "-c"] é uma instrução que define o shell padrão a ser usado durante a construção da imagem

    SHELL ["/bin/bash", "-c"]

Normalmente, o Docker usa o /bin/sh como shell padrão, mas nesta linha, estamos especificando que o /bin/bash será usado, com a opção -c para executar os comandos.

Isso é útil quando você precisa executar scripts bash ou usar recursos específicos do Bash durante a construção da imagem. Ao definir o Bash como shell padrão, você pode ter certeza de que todos os comandos e scripts serão executados corretamente.

Então, em resumo:

FROM ubuntu:22.04: Usa a imagem base do Ubuntu 22.04.
SHELL ["/bin/bash", "-c"]: Define o Bash como o shell padrão a ser usado durante a construção da imagem.
Essa combinação de instruções fornece uma base Ubuntu 22.04 com o Bash como shell padrão, o que pode ser útil em muitos casos de uso do Docker.

### Instrucao ARG
A instrução ARG em um Dockerfile é usada para definir uma variável de argumento que pode ser passada durante a construção da imagem.

Ela tem o seguinte formato:

    ARG <name>[=<default value>]

Onde:

- <name> é o nome da variável de argumento.

- <default value> é um valor padrão opcional para a variável.

Algumas características importantes sobre a instrução ARG:

- Acesso durante a construção: As variáveis de argumento definidas com ARG podem ser acessadas durante o processo de construção da imagem, ou seja, dentro das outras instruções do Dockerfile.

- Passagem de valores: Quando você executa o comando docker build, você pode passar valores para as variáveis de argumento usando a opção --build-arg <varname>=<value>.

- Valor padrão: Se um valor padrão for definido na instrução ARG, esse valor será usado caso nenhum valor seja passado durante a construção.

- Escopo: As variáveis de argumento têm escopo apenas durante a construção da imagem. Elas não são mantidas no contêiner resultante.

Exemplo de uso:

    ARG APP_VERSION=1.0
    FROM ubuntu:22.04
    COPY app_files /app
    RUN ./install_app.sh --version $APP_VERSION
Neste exemplo, APP_VERSION é definida como uma variável de argumento com um valor padrão de 1.0. Esse valor pode ser substituído durante a construção da imagem usando --build-arg APP_VERSION=2.0.

Dessa forma, a instrução RUN pode acessar o valor da variável APP_VERSION durante a construção da imagem.

A instrução ARG DEBIAN_FRONTEND=noninteractive é usada em Dockerfiles para definir uma variável de ambiente chamada DEBIAN_FRONTEND com o valor noninteractive.

    ARG DEBIAN_FRONTEND=noninteractive

Essa variável é específica para sistemas baseados no Debian, incluindo o Ubuntu, e tem o objetivo de evitar interações interativas durante a instalação de pacotes.

Quando o DEBIAN_FRONTEND é definido como noninteractive, os pacotes do Debian/Ubuntu serão instalados de forma não interativa, ou seja, sem exibir prompts ou perguntas que exigem entrada do usuário.

Isso é útil em ambientes de containerização, como o Docker, pois evita que o processo de construção da imagem fique travado esperando por interações do usuário.

Alguns benefícios de usar DEBIAN_FRONTEND=noninteractive em um Dockerfile:

- Automatização da construção: A construção da imagem fica totalmente automatizada, sem interrupções.

- Redução do tamanho da imagem: Ao evitar a instalação de pacotes desnecessários, o tamanho final da imagem Docker é menor.

- Reprodutibilidade: A construção da imagem fica mais determinística e reproduzível, pois não há dependência de intervenção humana.

Então, a instrução ARG DEBIAN_FRONTEND=noninteractive é uma forma de configurar o ambiente de construção do Dockerfile para que a instalação de pacotes Debian/Ubuntu seja feita de maneira não interativa.

### Instrucao ENV
Essas instruções ENV no Dockerfile definem várias variáveis de ambiente que podem ser úteis em um ambiente de desenvolvimento ou implantação de uma aplicação Python.

Vamos entender o que cada uma delas faz:

ENV GIT_SSL_NO_VERIFY=true

Essa variável desativa a verificação SSL/TLS ao usar o Git durante a construção da imagem. Isso pode ser útil se sua aplicação precisar fazer clonagem de repositórios Git que usam certificados auto-assinados.
ENV PYTHONDONTWRITEBYTECODE=1

Essa variável evita que o Python gere arquivos de bytecode .pyc durante a execução da aplicação. Isso pode ser útil para reduzir o tamanho da imagem Docker.
ENV PYTHONUNBUFFERED=1

Essa variável faz com que a saída do Python seja desejada sem buffering. Isso pode ajudar a obter um feedback mais imediato durante a execução da aplicação.
ENV PYTHONUTF8=1

Essa variável força o Python a usar a codificação UTF-8 por padrão. Isso é importante para garantir o correto manuseio de caracteres Unicode.
ENV PIP_NO_CACHE_DIR=off

Essa variável desativa o cache de pacotes do pip durante a instalação de dependências. Isso pode ser útil para forçar o download das últimas versões dos pacotes, evitando problemas de cache.
Essas configurações de variáveis de ambiente podem ajudar a melhorar o desempenho, o tamanho da imagem e o comportamento geral da sua aplicação Python em um ambiente Docker.

É importante entender o propósito de cada uma delas e avaliar se elas se aplicam ao seu caso de uso específico.

### Instrucao RUN
O comando que você mencionou é uma instrução RUN em um Dockerfile, e ele realiza as seguintes ações:

No caso 

    RUN apt-get update \
         && apt-get install --assume-yes --no-install-recommends ca-certificates

- apt-get update:

    - Essa parte do comando atualiza a lista de pacotes disponíveis no repositório do sistema operacional baseado em Debian (como o Ubuntu).

    - Isso é importante para garantir que os pacotes mais recentes estejam disponíveis para instalação.

- apt-get install --assume-yes --no-install-recommends ca-certificates:

    - Essa parte do comando instala o pacote ca-certificates.

    - A opção --assume-yes faz com que o comando seja executado de forma não interativa, aceitando automaticamente todas as confirmações necessárias.

    - A opção --no-install-recommends evita a instalação de pacotes recomendados, reduzindo o número de pacotes instalados e, consequentemente, o tamanho da imagem Docker.

    - O pacote ca-certificates é importante para fornecer os certificados de autoridade de certificação confiáveis, necessários para conexões HTTPS seguras.

Então, esse comando garante que a lista de pacotes esteja atualizada e instala o pacote ca-certificates, que é essencial para muitas aplicações que precisam se conectar a serviços web seguros.

Essa é uma prática comum em Dockerfiles, pois garante que a imagem tenha os pacotes básicos necessários para o funcionamento da aplicação, sem instalar pacotes desnecessários
