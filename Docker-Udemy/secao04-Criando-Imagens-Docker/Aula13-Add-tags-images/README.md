# Adicionando tags a imagens:
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