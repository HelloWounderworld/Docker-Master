# Utilizando o EXPOSE:
- O EXPOSE serve para conseguir definir qual porta para o localhost em que o container irá rodar. (Para a implementação que fizemos foi o EXPOSE 3000)

- Um detalhe muito importante. Quando acessamos o container localmente especificando uma porta, a especificação, somente, serve para dizer à máquina na qual estou rodando o container qual porta eu quero abrir para utilizar. Isso significa que não irei poder utilizar o ifconfig e acessar o mesmo app pelo outro aparelho mesmo que eu tenha o ip da máquina onde o container esta rodando.