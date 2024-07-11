# Copiando arquivos na imagem:
- Podemos colocar dentro do Dockerfile o COPY da forma (COPY yarn.lock, ou se quiser colocar mais conteúdo, COPY yarn.lock package.json)

- Uma segunda forma de uso é quando vc queira copiar um arquivo para dentro de um outro diretório, no caso, a estrutura exemplo seria COPY package.json /app (se for simples arquivo) ou COPY package.json /app/ (se for dois arquivos)

- Se quiser copiar todos os arquivos json dentro de um diretório, seria COPY *.json /app/

- Se quiser copiar todos os arquivos, seria COPY . /app/

- Se quiser definir que toda a execução ocorre somente dentro de um diretório, em vez de ficar especificando pelo COPY para qual diretório, antes disso bastaria colocar o WORKDIR /app, para especificar que tudo ocorrerá dentro do diretório app.

- A diferença entre COPY e o ADD está no fato de que se vc quiser realizar alguma implementação que esteja em algum web site, em vez do COPY, vc utilizará o ADD.

- No caso, se for uma cópia simples, usamos o COPY, mas se for uma cópia de um website ou arquivo zip, usamos o ADD.

- Implementado o WORKDIR e COPY no Dockerfile dentro do diretório app, bastaria rodar pelo terminal o mesmo comando para construir a imagem, mas desta vez com os WORKDIR e COPY implementados

- Desta vez, se rodarmos de forma interativa como foi feito antes, poderemos ver que a ação do COPY estará implementado de forma que vc colocando o comando ls, irá aparecer todos os arquivos que tem no diretório app copiados dentro da pasta interativa.