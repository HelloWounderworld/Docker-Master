# Volumes persistentes:
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