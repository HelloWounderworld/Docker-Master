# Salvando e carregando imagens:
- Podemo transferir sempre as imagens de uma máquina para outra por intermédio do docker hub, o que é recomendável. Mas existem formas mais diretas de realizar isso.

- docker image save --help

- Mostrará as opções para salvar

- docker image save -o appv2.tar app:v2

- Ao olhar na pasta/diretório app podemos ver o arquivo appv2.tar que é o arquivo comprimido onde foi salvo a imagem app v2

- docker image rm app:v2

- docker image rm (Image ID siglas iniciais)

- docker image load --help

- docker image load -i appv2.tar