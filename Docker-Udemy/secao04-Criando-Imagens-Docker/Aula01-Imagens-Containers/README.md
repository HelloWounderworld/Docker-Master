# O que são Imagens e Containers?:

## O que é Imagem:
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

## O que é Container:
- É como se fosse uma VM de forma isolado

- Ele tem start/stop

- É um processo que roda dentro de uma máquina