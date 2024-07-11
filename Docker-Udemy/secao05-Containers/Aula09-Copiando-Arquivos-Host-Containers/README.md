# Copiando arquivos de host para o container:
- Vamos aprender a copiar arquivos ou pasta que estão dentro de um container em execução de modo interativo para dentro de um container.

- docker exec -it (nome do contianer) sh - Executando um container no modo interativo.

- docker cp (origem) (destino) - docker cp kiwi2:/app/text.txt ., no caso a origem é kiwi2:/app/text.txt e o destino é no meu local ".".

- Com o mesmo comando acima, podemos criar uma cópia de um arquivo do local para alguma aplicação que roda de forma interativa.