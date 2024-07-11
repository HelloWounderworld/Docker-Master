# Melhorando a performance:
- Cada vez mais que add as dependências a imagem fica cada vez mais pesado para rodar ela ou até mesmo na sua criação. Existe uma maneira de deixar o processamento dessa imagem mais leve usando o cache.

- O formato como vc colocar o COPY no Dockerfile, ele pode melhorar a performance do processamento. No caso, colocando, por exemplo, o COPY package.json antes e depois o COPY . ., melhoramos a performance da construção da imagem, pois estamos verificando primeiro se o arquivo núcleo onde há todas as dependências houve ou não alguma alteração e se não tiver, então bastaria colocar da mesma forma como estava antes sem precisar passar novamente pelo processo de recriamento. Ou seja, estará tudo cacheado.

- No caso, ao acrescentarmos o arquivo README.txt, como não houve nenhuma alteração no package.json e o COPY package.json irá confirmar isso, então não será necessário rodar os dois RUNS que estão sendo pedidos para processar.

- Logo, em Dockerfile, podemos tornar melhor a performance do processamento só pela alteração da ordem que colocamos os comandos ou a forma como pedimos para que a imagem seja construída.