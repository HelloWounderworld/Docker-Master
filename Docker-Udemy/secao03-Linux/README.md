# Seção 03 - Linux:
  Se vc quiser manusear de forma bem feita o Docker, é inevitável que seja uma condição necessário que vc saiba muito bem Linux.

  Considerando que na sua máquina não tenha um Linux instalado, iremos aproveitar do recurso muito poderoso do Docker, o container.

  No caso, podemos, sim, rodar um Linux dentro de um container. O que significa que se vc tem um Sistema Operacional (SO) que não seja linux e precisa trabalhar com Linux, vc não precisará instalar uma na sua máquina e dividindo os espaços do disco rígido só para poder aproveitar dos recursos desse SO. Mas, sim, bastaria criar um container dentro do Docker e dentro dela rodar o Linux localmente.

  Vamos praticar alguns comandos:

- Primeiro, vamos verificar quais tipos de containers estão rodando no docker ou quantos containers foram criadas, o que inclui aquelas que não estão rodando mas estão lá, claro precisa estar com o Docker Desktop aberto:
    - docker ps - serve para verificar quais containers estão rodando

    - docker ps -a - Lista todos os containers existentes.

- Segundo, vamos pegar a distribuição Linux do Docker Hub rodando o comando pelo terminal. Vale ressaltar que a forma como será rodado o Ubuntu se chama modo interativo (interactive mode):
    - docker run -it (nome da ditribuição) - Não só baixa a distribuição como tbm já roda criando um terminal linux Ubuntu dentro do terminal que vc está utilizando

        Unable to find image 'ubuntu:latest' locally
        latest: Pulling from library/ubuntu
        cf92e523b49e: Pull complete 
        Digest: sha256:35fb073f9e56eb84041b0745cb714eff0f7b225ea9e024f703cab56aaa5c7720
        Status: Downloaded newer image for ubuntu:latest
        root@afd2ee4370ef:/#

    Exibição do resultado após rodar o comando acima. Basicamete, "root@afd2ee4370ef:/#" isso indica que está rodando um terminal linux Ubuntu dentro do terminal que vc está trabalhando.

    Para confirmação disso, bastaria colocar o comando "ls" nesse terminal Linux para verificar que serão exibidos diretórios que não constam na sua máquina.

    Experimentando alguns comandos:

    - whoami - Mostrará qual o nome do usuário cadastrado pelo terminal Linux

    - echo <string> - retorna o string

    - echo $0 - Me dirá em qual diretório estou. Neste caso, o bash

    - history - retornará o histórico de comandos que foi rodado pelo terminal

    - docker pull (nome da distribuição) - se fosse só para baixar alguma distribuição do Docker Hub

- Vamos agora aprender sobre pacotes que temos no Linux, o tal do apt (Advanced Packege Tool):
    - apt list - serve para verifica quais pacotes já estão instalados no Linux.

    - apt update - acessará o ubunto e realizará download dos pacotes mais utilizados e/ou mais atualizados

    - nano - é um pacote que que se for necessário usar ela precisaria instalar ela. Ela é um editor de texto.

    - apt install (nome do pacote) - Serve para instalar o pacote que vc precisa. No caso, instala o nano.

    - nano teste.txt - cria um arquivo de texto com o nome teste e extensão .txt. Porém precisa ser salvo usando os atalhos abaixo. Bastaria digitar ls para verificar que de fato o arquivo foi criado.

    - apt remove (nome do pacote) - remove o pacote instalado.

- Vamos agora aprender sobre o sistema de arquivos do Linux e suas hierarquias:
    - No Linux tudo começa com o root/barra, "/" (no windows essa barra é para o outro lado).

    - Depois da barra vem os diretórios, como bin, dev, etc, etc... Bastaria dar um ls para ver os tipos de diretórios disponíveis.

      - bin - foi criado para armazenar comandos binários que precisam ser disponíveis para todos os usuários. Como, por exemplo, os comandos que colocamos no terminal.

      - dev - é um espaço para armazenar os arquivos de devices/dispositivos como, por exemplo, NOU, disco, SDA, TTY, random, etc...

      - etc (editable text configuration) - é armazenado arquivos de hosts.

    - Para saber mais sobre bastaria colocar no google "linux directory structure" ou acessar diretamente um  desses links 
        
        https://www.thegeekstuff.com/2010/09/linux-file-system-structure/, https://www.geeksforgeeks.org/linux-directory-structure/
        https://eng.libretexts.org/Bookshelves/Computer_Science/Operating_Systems/Linux_-_The_Penguin_Marches_On_(McClanahan)/04%3A_Managing_Linux_Storage/5.12%3A_Linux_Directory_Structure/5.12.01%3A_Linux_Directory_Structure_-_Hierarchy

- Navegando no Linux:
    - pwd (print working directory) - Mostra o caminho de acessos aos diretórios começando do diretório principal, "/".
    - ls -1 - Mostra todos os arquivos e diretórios em forma de coluna e não em linha
    - ls -l - Mostra o diretório e o respectivo informação desse diretório.
    - cd /(nome do diretório) (Change Directory - cd) - Acessa o diretório que vc queira. Podemos ir colocando vários barras e os nomes dos diretórios que reside dentro de outro diretório, como por exemplo, cd /etc/alternative/(nome)/(nome)
    - cd .. - Serve para voltar um diretório anterior
    - ls /(nome do diretorio)/(nome do diretório dentro do diretório anterior) - Serve para listar os diretórios e o arquivo de um diretório específico.

- Criando Arquivos e Diretórios:
    - cd ~ - Serve para acessar o diretório home
    - mkdir (nome) - serve para criar uma pasta
    - mv (nome antigo) (nome novo) - serve para modificar o nome. O mesmo comando serve para modificar o arquivo de uma pasta para outro
    - touch (nome e extensão do arquivo) - Serve para criar um arquivo. Pode se criar vários arquivos colocando o nome o extensão de cada arquivo sucessivamente ao lado do outro separado por espaço.
    - rm (nome do arquivo) - remove o arquivo 
    - rm (siglas que iniciam)* - remove todo arquivo que inicia com tal sigla. Um exemplo que temos é hi1.txt, hi2.txt e hi3.txt. colocando o comando rm hi* todos os arquivos que começa com "hi" serão removidos.
    - rm -r (nome do diretório) - serve para remover o diretório.

- Editando arquivos:
    - cat (nome do arquivo) - serve para visualizar o conteúdo dentro do arquivo.
    - cat /(nome do diretório)/(nome do arquivo que está dentro do diretório) - Serve para conseguir visualizar o conteúdo/informação dentro do arquivo que reside dentro de um diretório.
    - more (caminho do diretorio e em seguida o nome do arquivo) - Mostrará somente 25% das informações contidas dentro do arquivo, dependendo do tamanho da janela do terminal aberto. Basta pressionar espaço para ir mostrando mais informações contidas dentro desse arquivo. Isso de cima para baixo.
    - less (caminho do diretorio e em seguida o nome do arquivo) - é o mesmo do more, mas de baixo para cima. Precisaria instalar o pacote que inclui esse comando dependendo a versão do Linux.

- Redirecionando no Linux:
    - cat (nome do arquivo) > (nome de um arquivo novo) - serve para criar um novo arquivo e mandar todas as informações que estão no arquivo existente e indicado no comando dentro desse novo arquivo. Podemos usar esse "cat" da outra forma tbm que é chamando dois arquivos ou mais arquivos existente e concatenar sobre um outro arquivo novo que será criado e dentro da mesma enviar todas as informações dos arquivos que foram chamados de forma concatenada. Um exemplo, cat leonardo.txt teste.txt > file.txt.
    - echo (alguma frase) > (nome de um arquivo novo) - Serve para poder colocar alguma frase dentro de um arquivo novo ou existente.

- Utilizando GREP: https://phoenixnap.com/kb/grep-command-linux-unix-examples
    - grep (Global Regular Expression Print) - Serve para conseguir verifiar se algum conteúdo está dentro de um arquivo sem preciar abrir o arquivo. Podemos realizar a procura de um conteúdo de forma simultânea em vários arquivos tbm. Bastaria chamar os nomes dos arquivos sucessivamente seguido de espaço.
    - grep (conteúdo) (sigla)* - Podemos a mesma procura que ocorre na exibição do comando cat usando *.
    - grep (conteúdo) . - Serve para verficar de forma booleana se existe ou não algum diretório com conteúdo que vc está colocando.
    - grep -i (conteúdo) . - -i pede para ignorar se é maiúsculo ou minúsculo
    - grep -i -r (conteudo) . - Serve para não só confirmar se existem arquivos com tais conteúdos com também exibem quais são.

- Utilizando o FIND:
    - find - Serve para procurar um arquivo. Até aqueles que estão ocultos.
    - find /(nome do diretório) - vai mostrar tudo que está dentro desse diretório.
    - find -type (f ou d) - filtra a procura por tipos, sendo "f" arquivos e "d" diretórios.
    - find -type f -name "(nome do arquivo e extensão dela)" - Serve para verficar se existe o arquivo com aquele nome. Diferencia letra maiúscula e minúscula. O mesmo vale para diretório, caso coloque o "d" no lugar de "f".
    - findo -type f -name "(siglas)*" - serve para procurar todos os arquivos que inicia com a tal sigla. O mesmo vale para o diretório caso coloque o "d" no lugar de "f".

- Execudando multiplos comandos:
    - Cada comando executado deverá ser separado por ";" em Linux.
    - O conjunto de comandos acima serão processados, todas elas, independente de se algum comando delas não rodar. Para caso vc queira que se, por ventura, algum dos comandos não rodar vc quiser que ele pare o processo, então no lugar de ";" deverá ser usado o "&&".

- Gerenciando processos:
    - ps - vc consegue visualizar os processos que estão rodando.
    - sleep (numero) - é uma forma de exibir a linha de comando do terminal após algum tempo.
    - sleep (numero) & - Executa o comando sleep, mas deixa o terminal livre. Esse processo é chamado de background. No caso, feito esse comando em seguida colocar o comando ps, será mostrado que o processo sleep está sendo executado.
    - kill (Número do PID que pode ser visto pelo ps) - Ele mata literalmente o processamento, ou seja, encerra, dá um freio bruto. Esse comando serve para casos em que o sistema operacional que vc está rodando está muito lento e serve para conseguir tirar algum processamento desnecessário que esteja rodando.

- Gerenciando Usuários:
    - useradd - Serve para poder add algum novo usuário e não basta somente esse comando. Mas tbm, precisaria colocar mais algum outro comando. Para verificar isso basta colocar useradd no terminal e dar o enter.
    - useradd -m (algum nome) - cria o usuário com o nome. Mas vc consegue fazer isso mediante de que vc seja o root.
    - usermod - serve para modificar o usuário.
    - userdel - serve para deletar o usuário.
    - cat /etc/passwd - Serve para verificar se o usuário foi criado, mas claro, o password será exibido de forma encriptada.
    - Precisamos saber como logar com o usuário que criamos dentro do SO interativo. Para isso precisamos abrir uma nova aba do terminal e dentro dela digitar "docker exec -it -u (nome do usuário criado) (Id do container onde está rodando o SO interativo) bash".
    - Ao logarmos com um usuário, ele terá alguns acessos negados, onde somente o usuário dono "root" tem.
    - exit - Para sair do modo de usuário logado.

- Gerenciando Grupos:
    - cat /etc/group - Serve para verificar quais grupos compostos de usuários existem.
    - Todo usuário criado pelo useradd acabam sendo adicionados aos grupos primários ou secundários.
    - groups (nome de algum grupo) - Mostrará todos os usuários pertencentes à esse grupo.
    - groupadd (nome do grupo novo) - Criará um novo grupo.
    - usermod -G (nome do grupo) (usuário que vc quer add) - Serve para adicionar um usuário em um determinado grupo.
    - groups (nome do usuário) - Mostrará em quais groups esse usuário pertence.
    
- Premissões de Arquivos: 
    - Quando damos ls -l, na lista é mostrado uma combinação de "r", "w", "d" e "x", respectivamente, read, write, directory e execute. Eles indicam os tipos de permissões que o usuário pode realizar sobre o arquivo, diretório e o programa que existem. Tudo isso no primeiro bloco que está dividido com um traço.
    - Agora, no segundo bloco, depois do traço de um conjunto de permissões, existe as permissões que os grupos existentes podem realizar.
    - Agora, no terceiro bloco, reside as permissões do "everyone", ou seja, as permissões que todo mundo tem.
    - chmod u+(alguma permissão) (arquivo que vc quer add a permissão) - Serve para add alguma permissão de um usuário sobre um arquivo.