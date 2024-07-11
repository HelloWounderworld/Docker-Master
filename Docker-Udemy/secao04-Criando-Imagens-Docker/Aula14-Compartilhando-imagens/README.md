# Compatilhando imagens:
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