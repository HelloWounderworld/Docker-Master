# Adicionando um usuário na imagem:
- RUN addgroup dev && adduser -S -G leonardo dev

- USER leonardo

- Colocamos o comando acima depois que o WORKDIR para conseguimos rodar os usuários que estão dentro do container que foi criado.

- Por hora não vamos precisar desses comandos acima para a finalidade de teste do app.