# Instruções do Dockerfile:
- Precisaremos criar um dockerfile dentro do diretório app.

    - FROM - Esse from indica qual imagem irá carregar, um windows, linux ubuntu, center OS, Alpine, etc... E qual que é a plataforma nodejs, python, etc...

    - WORKDIR (Working Directory) - Define em qual diretório quer que a sua aplicação rode sempre

    - COPY/ADD - Esses dois servem para copiar/adicionar todos os arquivos que fazem parte da sua aplicação dentro da sua imagem

    - RUN - diz para rodar tal processo

    - ENV (Enviroment) - Configuração do ambiente, no caso, o que eu preciso dentro do meu linux para rodar a tal aplicação.

    - EXPOSE - é o que é responsável colocar em qual porta local que vc escolheu para rodar a sua aplicação

    - USER - Define o usuário que pode rodar essa aplicação. O uso desse recurso é opcional.

    - CMD/ENTRYPOINT - Servem para vc poder rodar outros comandos que vc deseja implementar no processo de criação da imagem.

### OBS: Uma boa pratica de configurar um Dockerfile seria em utilizar, somente um FROM dentro dela!!!
Sim, é considerada uma boa prática utilizar apenas um comando FROM no início do Dockerfile. Essa abordagem é recomendada pelos guias oficiais de boas práticas para construção de imagens Docker.

Algumas razões pelas quais é preferível usar apenas um FROM no início do Dockerfile:

Simplicidade e Legibilidade: Ter apenas um comando FROM torna o Dockerfile mais simples e fácil de entender. Isso facilita a manutenção e a colaboração entre equipes.

Desempenho: Usar múltiplos comandos FROM pode aumentar o tempo de construção da imagem, pois cada etapa de FROM inicia uma nova camada no sistema de arquivos da imagem. Quanto menos camadas, mais rápida será a construção.

Rastreabilidade: Com apenas um FROM, fica mais fácil rastrear a origem da imagem base e entender a proveniência da imagem final.

Segurança: Usando apenas uma imagem base, é possível garantir que todas as atualizações de segurança e correções sejam aplicadas de forma consistente em toda a imagem.

Organização: Ao invés de ter múltiplas etapas de FROM, é preferível criar imagens intermediárias ou usar recursos como estágios de compilação (multi-stage builds) para separar diferentes fases da construção da imagem.

Embora existam casos específicos em que o uso de múltiplos comandos FROM pode ser justificado, a recomendação geral é seguir a abordagem de um único FROM no início do Dockerfile. Isso ajuda a manter a imagem Docker mais limpa, eficiente e fácil de entender e manter.

Há alguns casos em que pode ser adequado utilizar múltiplos comandos FROM dentro de um Dockerfile. Aqui estão alguns exemplos:

Multi-stage Builds: Essa é a principal razão para usar múltiplos FROM em um Dockerfile. A técnica de multi-stage builds permite separar o processo de construção em etapas independentes, usando diferentes imagens base. Isso é útil quando você precisa construir uma aplicação a partir de uma imagem maior e, em seguida, copiar apenas os artefatos necessários para uma imagem final menor e mais leve.

Construção de Aplicações Multilinguagem: Quando você precisa construir uma aplicação que envolve diferentes linguagens de programação (por exemplo, um backend em Python e um frontend em Node.js), usar múltiplos FROM pode ajudar a isolar e organizar melhor as etapas de construção.

Reutilização de Imagens Intermediárias: Em casos em que você precisa construir imagens complexas com muitas dependências, pode ser benéfico criar imagens intermediárias que possam ser reutilizadas em outros Dockerfiles. Isso ajuda a reduzir o tempo de construção e o tamanho da imagem final.

Testes e Validação: Você pode usar múltiplos FROM para criar etapas de teste e validação separadas da construção final da imagem. Isso facilita o processo de depuração e garantia de qualidade.

Imagens Customizadas: Algumas vezes, você pode precisar estender ou personalizar uma imagem base existente. Nesse caso, usar um segundo FROM pode ser uma abordagem adequada.

É importante notar que, mesmo quando múltiplos FROM são usados, é recomendado manter o Dockerfile o mais simples e legível possível. Evite abusar dessa prática, pois ela pode tornar o Dockerfile mais complexo e dificultar a manutenção.

Em resumo, o uso de múltiplos FROM é justificado principalmente em cenários de construção de aplicações complexas, onde a separação de etapas traz benefícios significativos em termos de desempenho, organização e manutenibilidade.