# Executando comandos em containers:
- Vamos ensinar uma forma de executar algum comando enquanto o container estiver rodando.

- docker exec (nome do container) ls - Estou executando depois que a imagem está carregado dentro do container. No caso, o comando exibirá todos os arquivos e diretórios disponíveis dentro da imagem que foi criado.

- docker exec (nome do container) (algum outro comando) - De modo geral, esse comando serve dessa forma para podermos verificar/modificar/criar algo dentro do linux sem acessar diretamento o linux.