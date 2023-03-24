# Seção 02 - O Docker:

## O que é Docker?:
O docker a funcionalidade dela se basea muito em containers. Basicamente, a sua funcionalidade pode ser tirado em analogia como um transporte de navios que carregam os containers. Ou seja, vc tem o seu ambiente local onde vc cria a sua aplicação, um exemplo do mundo concreto seria uma loja que estivesse criando algum imóvel próprio, em seguida vc pega essa sua aplicação e gera uma imagem dela, no moundo concreto é o momento em que vc está empacotando o imóvel que vc produziu, para, em seguida, vc enviar esse seu image para um container, que é o momento em que vc pega o pacote envia para um correio com o endereço de um outro país e que necessita que a carga seja transportada via um navio, para depois disso vc conseguir lançar isso em um ambiente de produção para que outras pessoas consigam consumir, que é o momento em que o teu pacote chega ao destinatário e é consumido. Basicamente, a analogia acima é de como funciona o docker, sendo que a única diferença com o exemplo concreto de uma loja, é que esse processo todo até chegar ao consumidor quem estará realizando seria vc no computador que vc estiver utilizando.

## DockerHub:

- Recomendamos em criar uma conta no Docker Hub, pois dentro dela existem, praticamente, todas as bibliotecas de linguagens de programação que pode ser acionado num container.

- Isso significa que vc não precisa ter o linux instalado dentro da sua máquina. Bastando o Docker instalado e com uma conta no Docker Hub, será possível rodar um container com a linguagem que vc quiser dentro dela.

## Implementação Simples:
Antes de seguir para os próximos passos, precisamos nos certificar que o nodejs está instalado no seu computador.

Um exemplo simples, de Hello World, que podemos realizar para isso é criando um app.js como foi feito acima. No caso, estaremos realizando alguma aplicação em nodejs. Assim, pelo terminal, podemos colocar o comando "node app.js" e será exibido o conteúdo dentro da pasta app.js, no caso, o console que printa no terminal o que está escrito dentro dele, Hi Docker.

Mas ainda não chegamos no ponto em que queremos, que é o Docker. Caso vc não tenha nenhum tipo de node instalado na sua máquina, provavelmente, o comando acima que no terminal não rodará e apareceria alguma mensagem do gênero "comando não encontrado". 

Entretanto, como foi visto, o docker tem uma gama enorme de bibliotecas que são compatíveis para as linguagens. Ou seja, significa que mesmo que vc não tenha um node instalado na sua máquina, bastaria dockerizar, em outras palavras, no processo de criação da imagem, que será usado um arquivo chamado Dockerfile, dentro dela podemos gerenciar um comando que ao criar a imagem, nesse processo, instale a linguagem que vc queira usar, nesse caso node e o alpine. Assim, a imagem criada, dentro dela, estará instalada essas linguagens para serem rodadas dentro do container.

No caso, vamos ver como podemos converter a aplicação em um image. Para isso, precisamos criar um arquivo chamado Dockerfile. Basicamente, o Dockerfile é o arquivo e o núcleo onde vc consegue gerenciar de qual forma vc vai querer que ocorra as conversões para image e que tipo de comandos vc quer que o terminal faça depois que ocorre alguns processos ou quais pastas vc quer considerar da aplicação, etc.... Ou seja, é o controle central onde vc pode falar quem vai ou não ser considerado e como será considerado para o processo de geração da imagem.

Criado o Dockerfile (vamos ter uma seção em que vamos estudar cada comando que foi implementado dentro do Dockerfile para entender o gerenciamento) vamos precisar colocar no terminal com o diretório aberto o comando "docker build -t hi-docker .", onde o "hi-docker" será o nome da minha imagem e o "." (ponto) para referenciar que a imagem deverá ser criado a partir do diretório em que eu estou aberto pelo terminal (diretório local), no caso, Docker.

Feito o processo acima, se vc abrir o Docker Desktop, na aba images constará a imagem que vc criou, hi-docker.

Podemos verificar as imagens que foram criado colocando o comando "docker images" pelo terminal. Esse comando listará todos as imagens foram criadas e estão sendo listadas exatamente da forma como se encontra no Docker Desktop.

No caso, dentro da imagem, hi-docker, que acabamos de criar, dentro dela foi colocado um comando para instalar uma linguagem x de programação na imagem que será criada e que será rodado no container do Docker.

Agora, vamos precisar rodar a imagem que criamos. No caso, precisamos rodar pelo terminal o comando "docker run (nome da imagem que foi criada)". Como resultado, ocorreu o mesmo que aconteceu quando eu rodei pelo terminal o comando "node app.js" visto que no iMac que estou usando tem o node instalado.

Além disso, quando olhamos pelo Docker Desktop na aba Containers, podemos verificar que foi criado um container para rodarmos a imagem que foi criado.

Visto que não temos o node.js criado na nossa máquina.
