# Escolhendo a imagem:
- A aplicação teste que baixamos do site da Docker, conseguimos verificar em que tipo de versões que o app está configurado para podermos instruir a construção Dockefile

- Configurado o Dockerfile no diretório app de acordo com a instrução (Neste caso só foi colocado FROM node:12-alpine), então bastaria rodar no terminal o comando docker build -t app .

- O comando acima serve para construir uma imagem

- Rodando o comando docker run -it app sh, ela irá rodar essa imagem de forma interativa e dentro dela poderemos verificar que tipo de versão do node estará presente dentro dela

- Para sair do modo interativo acima, bastaria digitar Ctrl/Command + c ou exit