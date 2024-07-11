# Verificando o log de eventos:
- docker logs --help - Mostrará todas as nomenclaturas que podem ser acrescentadas para o docker logs.

- docker logs (options) (container ID)

- docker logs -f (container id) - No caso, ele fica escutando o container, no sentido que qualquer ação que eu fizer dentro do app que está rodando desse container que eu indiquei no log será exibido.

- docker logs -n (algum número inteiro) - Mostrará a lista dos containers de baixo para cima na quantidade em que vc escolhe levando em consideração o id, pode ser a sigla inicial em que um conjunto de id`s tenham, para lista-las.

- docker logs (container id/sigla) - Mostrará todas as lista inteira do docker.

- docker logs -t (container id) - Mostrará o timestamp de quanto tais mensagens de cada logs estão acontecendo.

- Em boas práticas, o desenvolvedor conhece muito bem a importância de usar os logs para debugar e resolver os problemas! Então os estudos de logs pelos terminais de SAAS, no geral, merece uma atenção bem especial para a pessoa aprender bem e evitar dores de cabeças futuras.