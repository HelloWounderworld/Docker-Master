# Utilizando o CMD:
- No caso, iremos especificar ao CMD qual o arquivo que queremos que rode. (CMD ["node", "src/index.js"])

- A diferença entre o RUN e o CMD está no fato de que o RUN roda durante a construção da imagem. Já o CMD tem como funcionalidade somente depois que a imagem está criada, para inicialização da imagem ou durante em que a imagem esteja rodando.

- Note que o yarn, tbm, faz parte do programa app que estamos rodando, então precisamos rodar ela tbm de modo que ela faça parte da composição de uma imagem. Para isso, bastaria acrescentar RUN yarn install --production