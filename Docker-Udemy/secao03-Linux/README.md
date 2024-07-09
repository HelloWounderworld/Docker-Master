# Seção 03 - Linux:
Se vc quiser manusear de forma bem feita o Docker, é inevitável que seja uma condição necessário que vc saiba muito bem Linux.

Considerando que na sua máquina não tenha um Linux instalado, iremos aproveitar do recurso muito poderoso do Docker, o container.

No caso, podemos, sim, rodar um Linux dentro de um container. O que significa que se vc tem um Sistema Operacional (SO) que não seja linux e precisa trabalhar com Linux, vc não precisará instalar uma na sua máquina e dividindo os espaços do disco rígido só para poder aproveitar dos recursos desse SO. Mas, sim, bastaria criar um container dentro do Docker e dentro dela rodar o Linux localmente.

## Vamos praticar alguns comandos:

- Primeiro, vamos verificar quais tipos de containers estão rodando no docker ou quantos containers foram criadas, o que inclui aquelas que não estão rodando mas estão lá, claro precisa estar com o Docker Desktop aberto:

        docker ps
    
    serve para verificar quais containers estão rodando.

        docker ps -a
    
    Lista todos os containers existentes.

- Segundo, vamos pegar a distribuição Linux do Docker Hub rodando o comando pelo terminal. Vale ressaltar que a forma como será rodado o Ubuntu se chama modo interativo (interactive mode):
    
        docker run -it (nome da ditribuição, neste caso, apenas, "ubuntu")
        
    Não só baixa a distribuição como tbm já roda criando um terminal linux Ubuntu dentro do terminal que vc está utilizando

        Unable to find image 'ubuntu:latest' locally
        latest: Pulling from library/ubuntu
        cf92e523b49e: Pull complete 
        Digest: sha256:35fb073f9e56eb84041b0745cb714eff0f7b225ea9e024f703cab56aaa5c7720
        Status: Downloaded newer image for ubuntu:latest
        root@afd2ee4370ef:/#

Exibição do resultado após rodar o comando acima. Basicamete, "root@afd2ee4370ef:/#" isso indica que está rodando um terminal linux Ubuntu dentro do terminal que vc está trabalhando.

Claro, vc poderia apenas baixar o ubuntu tbm fazendo

    docker pull ubuntu

Para confirmação disso, bastaria colocar o comando "ls" nesse terminal Linux para verificar que serão exibidos diretórios que não constam na sua máquina.

## Experimentando alguns comandos:

- whoami - Mostrará qual o nome do usuário cadastrado pelo terminal Linux

- echo <string> - retorna o string

- echo $0 - Me dirá em qual diretório estou. Neste caso, o bash

- history - retornará o histórico de comandos que foi rodado pelo terminal

- docker pull (nome da distribuição) - se fosse só para baixar alguma distribuição do Docker Hub

## Vamos agora aprender sobre pacotes que temos no Linux, o tal do apt (Advanced Packege Tool):

- apt list - serve para verifica quais pacotes já estão instalados no Linux.

- apt update - acessará o ubunto e realizará download dos pacotes mais utilizados e/ou mais atualizados

- nano - é um pacote que que se for necessário usar ela precisaria instalar ela. Ela é um editor de texto.

- apt install (nome do pacote) - Serve para instalar o pacote que vc precisa. No caso, instala o nano.

- nano teste.txt - cria um arquivo de texto com o nome teste e extensão .txt. Porém precisa ser salvo usando os atalhos abaixo. Bastaria digitar ls para verificar que de fato o arquivo foi criado.

- apt remove (nome do pacote) - remove o pacote instalado.

## Vamos agora aprender sobre o sistema de arquivos do Linux e suas hierarquias:
Essas sao os principais diretorios que encontramos no Linux

- /: O diretório raiz, que é o ponto de partida de toda a estrutura de diretórios.

- bin: foi criado para armazenar comandos binários que precisam ser disponíveis para todos os usuários. Como, por exemplo, os comandos que colocamos no terminal.

- sbin: Contém os comandos e utilitários de administração do sistema, geralmente acessíveis apenas ao superusuário (root).

- dev: é um espaço para armazenar os arquivos de devices/dispositivos como, por exemplo, NOU, disco, SDA, TTY, random, etc...

- etc (editable text configuration): é armazenado arquivos de hosts.

- home: Diretório que armazena os diretórios pessoais dos usuários do sistema.

- lib: Contém as bibliotecas compartilhadas essenciais para o funcionamento do sistema.

- media: Local onde são montados os dispositivos de armazenamento removíveis, como unidades USB e CDs/DVDs.

- mnt: Usado para montar temporariamente sistemas de arquivos.

- opt: Diretório destinado à instalação de aplicativos opcionais.

- proc: Contém informações sobre os processos em execução no sistema.

- root: Diretório pessoal do superusuário (root).

- run: Contém informações sobre o sistema em execução, como sockets e arquivos de bloqueio.

- srv: Contém informações sobre o sistema em execução, como sockets e arquivos de bloqueio.

- tmp: Diretório para arquivos temporários.

- urs: Contém aplicativos, bibliotecas e arquivos de dados de uso geral.

- var: iretório para arquivos de log, cache, spool e outros dados variáveis.

- boot: Contém os arquivos necessários para o boot do sistema, como o kernel, o initramfs e o gerenciador de boot.s

Agora, iremos explicar, uma por uma, a sua importancia.

### Diretorio bin
O diretório "/bin" (abreviação de "binaries") é um diretório muito importante nos sistemas operacionais baseados em Linux e Unix. Ele desempenha um papel fundamental no funcionamento do sistema. Aqui estão algumas informações sobre a importância do diretório "/bin":

1. Armazenamento de comandos essenciais:

    - O diretório "/bin" contém os principais comandos e utilitários do sistema operacional, como "ls", "cd", "mkdir", "rm", "cp", entre outros.

    - Esses comandos são fundamentais para a interação do usuário com o sistema e a execução de tarefas básicas.

2. Acesso rápido e eficiente:

    - O "/bin" está localizado no caminho padrão do sistema, o que significa que os comandos armazenados nele podem ser executados diretamente, sem a necessidade de especificar o caminho completo.

    - Isso torna a interação com o sistema mais rápida e eficiente, pois os usuários podem acessar esses comandos essenciais de qualquer lugar do sistema.

3. Inicialização do sistema:

    - Muitos dos comandos e programas necessários para a inicialização e o boot do sistema operacional estão localizados no diretório "/bin".

    - Isso inclui programas como o "init", que é o processo de inicialização do sistema, e o "bash", que é o shell padrão em muitas distribuições Linux.

4. Compatibilidade e portabilidade:

    - O conteúdo do diretório "/bin" é padronizado entre as diferentes distribuições Linux e sistemas Unix.

    - Isso garante a compatibilidade e a portabilidade de scripts e aplicativos que dependem desses comandos essenciais, facilitando a migração entre diferentes sistemas.

5. Segurança e controle de acesso:

    - O diretório "/bin" é geralmente de propriedade do superusuário (root) e possui permissões de acesso restritas.

    - Isso ajuda a proteger os comandos essenciais do sistema contra modificações acidentais ou maliciosas, contribuindo para a segurança geral do sistema.

Em resumo, o diretório "/bin" é um local crucial nos sistemas operacionais baseados em Linux e Unix, pois abriga os principais comandos e utilitários necessários para o funcionamento básico do sistema, garantindo a eficiência, a compatibilidade e a segurança do ambiente.

#### Uso direto do diretorio bin
Vou fornecer um exemplo simples da utilização direta do diretório "/bin" para executar comandos no Linux.

Suponha que você queira listar o conteúdo de um diretório. Você pode usar o comando "ls" para isso. No Linux, o comando "ls" está localizado no diretório "/bin".

Aqui está como você pode executar o comando "ls" diretamente a partir do diretório "/bin":

    /bin/ls

Ao digitar esse comando no terminal, o sistema operacional irá executar o programa "ls" localizado no diretório "/bin", listando o conteúdo do diretório atual.

Você também pode usar o comando "ls" sem especificar o caminho completo, pois o diretório "/bin" está incluído no PATH (variável de ambiente que define os diretórios onde o sistema procura por comandos executáveis).

Outro exemplo seria o uso do comando "cat" para exibir o conteúdo de um arquivo. O comando "cat" também está localizado no diretório "/bin":

    /bin/cat arquivo.txt

Ou, de forma mais simples:

    cat arquivo.txt

Nesse caso, o sistema irá encontrar e executar o comando "cat" no diretório "/bin" para exibir o conteúdo do arquivo "arquivo.txt".

Esses são apenas alguns exemplos simples de como você pode utilizar diretamente o diretório "/bin" para executar comandos essenciais no sistema operacional Linux. Essa capacidade de acessar diretamente os comandos importantes do sistema é uma das características-chave do Linux e de outros sistemas operacionais baseados em Unix.

### Diretorio sbin
O diretório "/sbin" (abreviação de "system binaries") é um diretório muito importante no sistema operacional Linux, especialmente no Ubuntu. Ele desempenha um papel fundamental na administração e manutenção do sistema. Vamos explorar em detalhes a importância e a utilidade desse diretório:

1. Comandos de administração do sistema:

    - O diretório "/sbin" contém os principais comandos e utilitários de administração do sistema, como "shutdown", "reboot", "mount", "ifconfig", "iptables", entre outros.

    - Esses comandos são essenciais para tarefas de gerenciamento, configuração e manutenção do sistema operacional.

2. Acesso restrito:

    - Por padrão, o acesso ao diretório "/sbin" é restrito aos usuários com privilégios de superusuário (root) ou a usuários com permissões específicas.

    - Essa restrição de acesso é uma medida de segurança importante, pois os comandos nesse diretório podem ter um impacto significativo no funcionamento do sistema.

3. Inicialização e boot do sistema:

    - Muitos dos programas necessários para o processo de inicialização e boot do sistema operacional estão localizados no "/sbin".

    - Isso inclui comandos como "init", "udevd" e "systemd-journald", que são fundamentais para o arranque e a execução do sistema.

4. Gerenciamento de serviços e processos:

    - O "/sbin" contém utilitários essenciais para o gerenciamento de serviços e processos no sistema, como "systemctl", "service" e "killall".

    - Esses comandos permitem que os administradores do sistema iniciem, parem, reiniciem e monitorem os serviços em execução.

5. Configuração de rede e segurança:

    - Comandos relacionados à configuração de rede, como "ifconfig", "route" e "iptables", estão localizados no diretório "/sbin".

    - Esses utilitários são fundamentais para a configuração e o gerenciamento de interfaces de rede, roteamento e regras de firewall.

6. Gerenciamento de dispositivos e sistemas de arquivos:

    - O "/sbin" contém comandos para o gerenciamento de dispositivos e sistemas de arquivos, como "fdisk", "mkfs" e "fsck".

    - Esses utilitários permitem que os administradores criem, modifiquem e verifiquem a integridade dos sistemas de arquivos.

Em resumo, o diretório "/sbin" é essencial para a administração e manutenção do sistema operacional Linux Ubuntu. Ele abriga os comandos e utilitários necessários para tarefas de gerenciamento, configuração, inicialização e segurança do sistema, sendo acessível apenas aos usuários com privilégios de superusuário (root) ou com permissões específicas. Essa restrição de acesso é uma medida de segurança importante para preservar a integridade e o funcionamento adequado do sistema.

#### Exemplo de utilizacao do sbin
Vamos supor que você queira reiniciar o sistema operacional. Para isso, você pode usar o comando "reboot", que está localizado no diretório "/sbin".

Você pode executar o comando "reboot" diretamente a partir do diretório "/sbin" da seguinte maneira:

    /sbin/reboot

Ao digitar esse comando no terminal, o sistema operacional irá executar o programa "reboot" localizado no diretório "/sbin" e reiniciar o sistema.

Outro exemplo seria o uso do comando "ifconfig" para configurar uma interface de rede. O comando "ifconfig" também está localizado no diretório "/sbin":

    /sbin/ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up

Nesse caso, o comando "/sbin/ifconfig" é usado para configurar a interface de rede "eth0" com o endereço IP "192.168.1.100" e a máscara de sub-rede "255.255.255.0", e ativar a interface.

É importante notar que, para executar esses comandos localizados no diretório "/sbin", você geralmente precisará ter privilégios de superusuário (root) ou usar o comando "sudo" para elevar temporariamente seus privilégios. Isso se deve ao fato de que os comandos nesse diretório são considerados essenciais para a administração e manutenção do sistema operacional, e seu uso inadequado pode causar problemas graves.

Portanto, o uso direto do diretório "/sbin" é geralmente restrito a administradores do sistema que precisam executar tarefas de gerenciamento e configuração avançadas do Linux.

### Diretorio dev
O diretório "/dev" é um diretório fundamental no sistema operacional Linux, incluindo o Ubuntu. Ele desempenha um papel essencial na forma como o sistema lida com dispositivos e recursos de hardware. Vamos explorar em detalhes a importância e a utilidade desse diretório:

1. Representação de dispositivos de hardware:

    - O diretório "/dev" contém arquivos especiais que representam os diferentes dispositivos de hardware conectados ao sistema, como discos rígidos, unidades de CD/DVD, portas seriais, dispositivos de rede, entre outros.

    - Esses arquivos especiais são chamados de "arquivos de dispositivo" e permitem que o sistema operacional interaja diretamente com os dispositivos físicos.

2. Acesso a dispositivos:

    - Os programas e aplicativos no sistema operacional acessam os dispositivos de hardware por meio dos arquivos de dispositivo localizados em "/dev".

    - Isso significa que, em vez de acessar diretamente o hardware, os programas interagem com os arquivos de dispositivo, que servem como uma camada de abstração entre o software e o hardware.

3. Criação dinâmica de arquivos de dispositivo:

    - O diretório "/dev" não contém apenas arquivos estáticos, mas também arquivos de dispositivo criados dinamicamente pelo sistema operacional.

    - Quando um novo dispositivo é conectado ao sistema, o kernel do Linux cria automaticamente um novo arquivo de dispositivo correspondente em "/dev" para permitir o acesso a esse dispositivo.

4. Gerenciamento de dispositivos:

    - Ferramentas de gerenciamento de dispositivos, como "udev", utilizam o diretório "/dev" para criar, modificar e remover arquivos de dispositivo de acordo com as alterações no hardware.

    - Isso garante que os programas e aplicativos possam acessar os dispositivos de maneira confiável e consistente.

5. Compatibilidade com aplicativos:

    - Muitos aplicativos e programas no sistema operacional Linux dependem da existência e do acesso aos arquivos de dispositivo em "/dev" para funcionar corretamente.

    - Essa dependência garante a compatibilidade entre o software e o hardware, permitindo que os aplicativos interajam com os dispositivos de maneira padronizada.

6. Segurança e permissões:

    - O acesso aos arquivos de dispositivo em "/dev" é controlado por permissões do sistema de arquivos, permitindo que apenas os usuários ou processos autorizados possam interagir com determinados dispositivos.

    - Essa camada de segurança é importante para evitar acessos indevidos e proteger a integridade do sistema.

Em resumo, o diretório "/dev" é essencial no sistema operacional Linux, pois ele fornece uma interface padronizada entre o software e o hardware, permitindo que os programas acessem e interajam com os dispositivos de maneira confiável e segura. Ele desempenha um papel fundamental no gerenciamento de dispositivos e na garantia da compatibilidade entre aplicativos e hardware no sistema.

#### Exemplos em que esse diretorio atua no sistema Linux
1. Acesso a dispositivos de armazenamento:

    - Quando você conecta um disco rígido ou uma unidade USB ao seu computador Linux, o sistema operacional cria um arquivo de dispositivo correspondente em "/dev".

    - Por exemplo, um disco rígido pode ser representado por "/dev/sda", e suas partições podem ser acessadas como "/dev/sda1", "/dev/sda2" e assim por diante.

    - Programas de gerenciamento de arquivos, como o Nautilus no Ubuntu, acessam esses arquivos de dispositivo para permitir que você monte, acesse e manipule os dados armazenados nesses dispositivos.

2. Interação com dispositivos de entrada/saída:

    - O diretório "/dev" também contém arquivos de dispositivo para dispositivos de entrada e saída, como teclados, mouses e monitores.

    - Por exemplo, o teclado padrão pode ser acessado por meio do arquivo "/dev/input/by-path/platform-i8042-serio-0-event-kbd".

    - Aplicativos que precisam interagir com esses dispositivos, como gerenciadores de janelas e ambientes de desktop, acessam os arquivos de dispositivo correspondentes em "/dev" para receber e processar os eventos gerados por esses dispositivos.

3. Gerenciamento de dispositivos de rede:

    - O diretório "/dev" também contém arquivos de dispositivo para interfaces de rede, como adaptadores Ethernet e interfaces Wi-Fi.

    - Esses arquivos de dispositivo, como "/dev/eth0" ou "/dev/wlan0", permitem que os programas de rede, como o NetworkManager, configurem e gerenciem as conexões de rede do sistema.

    - Ao interagir com esses arquivos de dispositivo, os programas podem obter informações sobre o status da rede, configurar endereços IP, ativar ou desativar interfaces e muito mais.

Esses são apenas alguns exemplos de como o diretório "/dev" atua no sistema operacional Linux. Ele fornece uma camada de abstração entre o software e o hardware, permitindo que os programas acessem e interajam com os diversos dispositivos conectados ao sistema de maneira padronizada e segura.

#### Exemplos em que esse diretorio atua diretamente
1. Acesso a dispositivos de armazenamento:

    - Você pode acessar diretamente um dispositivo de armazenamento, como um disco rígido, usando o arquivo de dispositivo correspondente em "/dev".

    - Por exemplo, para listar o conteúdo do primeiro disco rígido (geralmente /dev/sda), você pode usar o comando:

            ls -l /dev/sda

    - Você também pode montar diretamente um sistema de arquivos em um dispositivo de armazenamento usando o comando "mount":

            mount /dev/sda1 /mnt

    - Isso montará a primeira partição do primeiro disco rígido (geralmente /dev/sda1) no ponto de montagem "/mnt".

2. Interação com dispositivos de entrada/saída:

    - Você pode interagir diretamente com dispositivos de entrada, como o teclado, usando os arquivos de dispositivo em "/dev".

    - Por exemplo, para enviar um evento de teclado (como a pressão da tecla "Enter") diretamente para o dispositivo de teclado, você pode usar o comando:

            echo -n -e "\n" > /dev/input/by-path/platform-i8042-serio-0-event-kbd

    - Esse comando envia o caractere de nova linha (Enter) diretamente para o dispositivo de teclado.

3. Gerenciamento de dispositivos de rede:

    - Você pode configurar diretamente as interfaces de rede usando os arquivos de dispositivo em "/dev".

    - Você pode configurar diretamente as interfaces de rede usando os arquivos de dispositivo em "/dev".

            ip link set dev eth0 up
            ip addr add 192.168.1.100/24 dev eth0

    - Esses comandos interagem diretamente com o arquivo de dispositivo "/dev/eth0" para ativar a interface de rede e configurar o endereço IP.

É importante observar que o acesso direto aos arquivos de dispositivo em "/dev" geralmente requer privilégios de superusuário (root) ou o uso do comando "sudo". Isso se deve ao fato de que esses arquivos representam dispositivos de hardware sensíveis, e o acesso inadequado pode causar problemas no sistema.

Portanto, o uso direto do diretório "/dev" é geralmente restrito a administradores do sistema que precisam realizar tarefas avançadas de gerenciamento e configuração de dispositivos no Linux.

### Diretorio etc
O diretório "/etc" é um dos mais importantes e fundamentais no sistema operacional Linux e Unix. Ele desempenha um papel crucial na configuração e gerenciamento do sistema. Vamos explorar em detalhes a importância e a utilidade desse diretório:

1. Arquivos de configuração do sistema:

    - O diretório "/etc" contém a maioria dos arquivos de configuração do sistema operacional, aplicativos e serviços.

    - Esses arquivos de configuração definem o comportamento e as preferências do sistema, como configurações de rede, serviços de inicialização, permissões de arquivo, configurações de segurança, entre outros.

    - Exemplos de arquivos de configuração importantes incluem "/etc/fstab" (configurações de montagem de sistemas de arquivos), "/etc/passwd" (informações de usuários) e "/etc/nginx/nginx.conf" (configurações do servidor web Nginx).

2. Gerenciamento de serviços e daemons:

    - O diretório "/etc" abriga arquivos de configuração e scripts de inicialização para os principais serviços e daemons do sistema operacional.

    - Esses arquivos permitem que os administradores do sistema iniciem, parem, reiniciem e configurem os serviços em execução, como o servidor web Apache, o servidor de banco de dados MySQL, o serviço de firewall iptables, entre outros.

    - Exemplos de arquivos e diretórios relacionados a serviços incluem "/etc/systemd/system/" (arquivos de unidade do systemd), "/etc/init.d/" (scripts de inicialização de serviços) e "/etc/xinetd.d/" (configurações de serviços de rede).

4. Configurações de rede e segurança:

    - O diretório "/etc" contém arquivos de configuração relacionados à rede e à segurança do sistema, como "/etc/hosts" (mapeamento de nomes de host para endereços IP), "/etc/resolv.conf" (configurações de servidores DNS) e "/etc/ssh/sshd_config" (configurações do servidor SSH).

    - Esses arquivos de configuração permitem que os administradores controlem e personalizem o comportamento da rede e os aspectos de segurança do sistema operacional.

5. Configurações de hardware e drivers:

    - Alguns arquivos de configuração relacionados a hardware e drivers de dispositivos também são armazenados em "/etc", como "/etc/modprobe.d/" (configurações de módulos do kernel) e "/etc/udev/rules.d/" (regras de gerenciamento de dispositivos).

    - Esses arquivos permitem que os administradores personalizem o comportamento e o carregamento de drivers de dispositivos no sistema.

6. Arquivos de configuração de aplicativos:

    - Além das configurações do sistema operacional, o diretório "/etc" também abriga arquivos de configuração para muitos aplicativos e serviços instalados no sistema.

    - Esses arquivos permitem que os usuários e administradores personalizem o comportamento e as preferências de aplicativos, como servidores web, servidores de banco de dados, ferramentas de linha de comando, entre outros.

7. Centralização e organização de configurações:

    - O diretório "/etc" serve como um ponto central para armazenar e organizar a maioria das configurações do sistema operacional e aplicativos.

    - Essa centralização facilita a localização, edição e backup das configurações, tornando a administração do sistema mais eficiente.
    
Em resumo, o diretório "/etc" é essencial no sistema operacional Linux e Unix, pois ele abriga a maior parte das configurações e definições que controlam o comportamento do sistema operacional, serviços, aplicativos e hardware. Sua importância se deve à sua capacidade de centralizar e organizar as configurações, permitindo que os administradores gerenciem e personalizem o sistema de maneira eficiente.

#### Exemplos praticos de sua aplicacao
Vamos supor que você queira configurar o servidor web Apache em um sistema Linux. Para isso, você precisará acessar e editar os arquivos de configuração do Apache, que estão localizados no diretório "/etc".

Aqui está um exemplo passo a passo de como você pode utilizar o diretório "/etc" para configurar o Apache:

1. Localizar o arquivo de configuração do Apache:

    - O arquivo de configuração principal do Apache geralmente fica localizado em "/etc/apache2/apache2.conf" (para sistemas baseados em Debian, como Ubuntu) ou em "/etc/httpd/conf/httpd.conf" (para sistemas baseados em Red Hat, como CentOS).

2. Editar o arquivo de configuração:

    - Abra o arquivo de configuração do Apache usando um editor de texto, como o "nano" ou o "vim":

            sudo nano /etc/apache2/apache2.conf

    - Nesse arquivo, você pode encontrar diversas diretivas de configuração, como a porta em que o servidor web irá escutar, os diretórios raiz dos sites, as configurações de segurança, entre outras.

    - Faça as alterações necessárias de acordo com suas necessidades, como alterar a porta padrão do Apache de 80 para 8080.

3. Reiniciar o serviço do Apache:

    - Após salvar as alterações no arquivo de configuração, você precisará reiniciar o serviço do Apache para que as novas configurações sejam aplicadas:

            sudo systemctl restart apache2

4. Verificar o status do serviço:

    - Você pode verificar o status do serviço do Apache para garantir que ele está em execução e funcionando corretamente:

            sudo systemctl status apache2

Neste exemplo, você utilizou o diretório "/etc" para acessar e editar o arquivo de configuração principal do Apache, que controla o comportamento e as configurações desse servidor web. Essa é apenas uma das muitas aplicações práticas do diretório "/etc" no sistema operacional Linux.

Outros exemplos incluiriam a edição de arquivos de configuração de serviços de rede, como o "/etc/hosts" e o "/etc/resolv.conf", ou a configuração de permissões de usuários e grupos no arquivo "/etc/passwd" e "/etc/group".

O diretório "/etc" é essencial para a administração e personalização do sistema operacional Linux, pois ele centraliza a maioria das configurações que controlam o comportamento do sistema e dos aplicativos instalados.

### Referencias
E importante que, alem da abordagem introdutoria acima, seja feita uma leitura firme sobre o assunto.

Para saber mais sobre bastaria colocar no google "linux directory structure" ou acessar diretamente um  desses links
    
    https://www.thegeekstuff.com/2010/09/linux-file-system-structure/
    
    https://www.geeksforgeeks.org/linux-directory-structure/

    https://eng.libretexts.org/Bookshelves/Computer_Science/Operating_Systems/Linux_-_The_Penguin_Marches_On_(McClanahan)/04%3A_Managing_Linux_Storage/5.12%3A_Linux_Directory_Structure/5.12.01%3A_Linux_Directory_Structure_-_Hierarchy

## Navegando no Linux:
- pwd (print working directory) - Mostra o caminho de acessos aos diretórios começando do diretório principal, "/".

- ls -1 - Mostra todos os arquivos e diretórios em forma de coluna e não em linha

- ls -l - Mostra o diretório e o respectivo informação desse diretório.

- cd /(nome do diretório) (Change Directory - cd) - Acessa o diretório que vc queira. Podemos ir colocando vários barras e os nomes dos diretórios que reside dentro de outro diretório, como por exemplo, cd /etc/alternative/(nome)/(nome)

- cd .. - Serve para voltar um diretório anterior

- ls /(nome do diretorio)/(nome do diretório dentro do diretório anterior) - Serve para listar os diretórios e o arquivo de um diretório específico.

## Criando Arquivos e Diretórios:
- cd ~ - Serve para acessar o diretório home

- mkdir (nome) - serve para criar uma pasta

- mv (nome antigo) (nome novo) - serve para modificar o nome. O mesmo comando serve para modificar o arquivo de uma pasta para outro

- touch (nome e extensão do arquivo) - Serve para criar um arquivo. Pode se criar vários arquivos colocando o nome o extensão de cada arquivo sucessivamente ao lado do outro separado por espaço.

- rm (nome do arquivo) - remove o arquivo 

- rm (siglas que iniciam)* - remove todo arquivo que inicia com tal sigla. Um exemplo que temos é hi1.txt, hi2.txt e hi3.txt. colocando o comando rm hi* todos os arquivos que começa com "hi" serão removidos.

- rm -r (nome do diretório) - serve para remover o diretório.

## Editando arquivos:
- cat (nome do arquivo) - serve para visualizar o conteúdo dentro do arquivo.

- cat /(nome do diretório)/(nome do arquivo que está dentro do diretório) - Serve para conseguir visualizar o conteúdo/informação dentro do arquivo que reside dentro de um diretório.

- more (caminho do diretorio e em seguida o nome do arquivo) - Mostrará somente 25% das informações contidas dentro do arquivo, dependendo do tamanho da janela do terminal aberto. Basta pressionar espaço para ir mostrando mais informações contidas dentro desse arquivo. Isso de cima para baixo.

- less (caminho do diretorio e em seguida o nome do arquivo) - é o mesmo do more, mas de baixo para cima. Precisaria instalar o pacote que inclui esse comando dependendo a versão do Linux.

## Redirecionando no Linux:
- cat (nome do arquivo) > (nome de um arquivo novo) - serve para criar um novo arquivo e mandar todas as informações que estão no arquivo existente e indicado no comando dentro desse novo arquivo. Podemos usar esse "cat" da outra forma tbm que é chamando dois arquivos ou mais arquivos existente e concatenar sobre um outro arquivo novo que será criado e dentro da mesma enviar todas as informações dos arquivos que foram chamados de forma concatenada. Um exemplo, cat leonardo.txt teste.txt > file.txt.

- echo (alguma frase) > (nome de um arquivo novo) - Serve para poder colocar alguma frase dentro de um arquivo novo ou existente.

## Utilizando GREP: https://phoenixnap.com/kb/grep-command-linux-unix-examples

- grep (Global Regular Expression Print) - Serve para conseguir verifiar se algum conteúdo está dentro de um arquivo sem preciar abrir o arquivo. Podemos realizar a procura de um conteúdo de forma simultânea em vários arquivos tbm. Bastaria chamar os nomes dos arquivos sucessivamente seguido de espaço.

- grep (conteúdo) (sigla)* - Podemos a mesma procura que ocorre na exibição do comando cat usando *.

- grep (conteúdo) . - Serve para verficar de forma booleana se existe ou não algum diretório com conteúdo que vc está colocando.

- grep -i (conteúdo) . - -i pede para ignorar se é maiúsculo ou minúsculo

- grep -i -r (conteudo) . - Serve para não só confirmar se existem arquivos com tais conteúdos com também exibem quais são.

## Utilizando o FIND:
- find - Serve para procurar um arquivo. Até aqueles que estão ocultos.

- find /(nome do diretório) - vai mostrar tudo que está dentro desse diretório.

- find -type (f ou d) - filtra a procura por tipos, sendo "f" arquivos e "d" diretórios.

- find -type f -name "(nome do arquivo e extensão dela)" - Serve para verficar se existe o arquivo com aquele nome. Diferencia letra maiúscula e minúscula. O mesmo vale para diretório, caso coloque o "d" no lugar de "f".

- findo -type f -name "(siglas)*" - serve para procurar todos os arquivos que inicia com a tal sigla. O mesmo vale para o diretório caso coloque o "d" no lugar de "f".

## Execudando multiplos comandos:
- Cada comando executado deverá ser separado por ";" em Linux.

- O conjunto de comandos acima serão processados, todas elas, independente de se algum comando delas não rodar. Para caso vc queira que se, por ventura, algum dos comandos não rodar vc quiser que ele pare o processo, então no lugar de ";" deverá ser usado o "&&".

## Gerenciando processos:
- ps - vc consegue visualizar os processos que estão rodando.

- sleep (numero) - é uma forma de exibir a linha de comando do terminal após algum tempo.

- sleep (numero) & - Executa o comando sleep, mas deixa o terminal livre. Esse processo é chamado de background. No caso, feito esse comando em seguida colocar o comando ps, será mostrado que o processo sleep está sendo executado.

- kill (Número do PID que pode ser visto pelo ps) - Ele mata literalmente o processamento, ou seja, encerra, dá um freio bruto. Esse comando serve para casos em que o sistema operacional que vc está rodando está muito lento e serve para conseguir tirar algum processamento desnecessário que esteja rodando.

## Gerenciando Usuários:
- useradd - Serve para poder add algum novo usuário e não basta somente esse comando. Mas tbm, precisaria colocar mais algum outro comando. Para verificar isso basta colocar useradd no terminal e dar o enter.

- useradd -m (algum nome) - cria o usuário com o nome. Mas vc consegue fazer isso mediante de que vc seja o root.

- usermod - serve para modificar o usuário.

- userdel - serve para deletar o usuário.

- cat /etc/passwd - Serve para verificar se o usuário foi criado, mas claro, o password será exibido de forma encriptada.

- Precisamos saber como logar com o usuário que criamos dentro do SO interativo. Para isso precisamos abrir uma nova aba do terminal e dentro dela digitar "docker exec -it -u (nome do usuário criado) (Id do container onde está rodando o SO interativo) bash".

- Ao logarmos com um usuário, ele terá alguns acessos negados, onde somente o usuário dono "root" tem.

- exit - Para sair do modo de usuário logado.

## Gerenciando Grupos:
- cat /etc/group - Serve para verificar quais grupos compostos de usuários existem.

- Todo usuário criado pelo useradd acabam sendo adicionados aos grupos primários ou secundários.

- groups (nome de algum grupo) - Mostrará todos os usuários pertencentes à esse grupo.

- groupadd (nome do grupo novo) - Criará um novo grupo.

- usermod -G (nome do grupo) (usuário que vc quer add) - Serve para adicionar um usuário em um determinado grupo.

- groups (nome do usuário) - Mostrará em quais groups esse usuário pertence.
    
## Premissões de Arquivos: 
- Quando damos ls -l, na lista é mostrado uma combinação de "r", "w", "d" e "x", respectivamente, read, write, directory e execute. Eles indicam os tipos de permissões que o usuário pode realizar sobre o arquivo, diretório e o programa que existem. Tudo isso no primeiro bloco que está dividido com um traço.

- Agora, no segundo bloco, depois do traço de um conjunto de permissões, existe as permissões que os grupos existentes podem realizar.

- Agora, no terceiro bloco, reside as permissões do "everyone", ou seja, as permissões que todo mundo tem.

- chmod u+(alguma permissão) (arquivo que vc quer add a permissão) - Serve para add alguma permissão de um usuário sobre um arquivo.

### chown
Certainly! The chown command in Linux is used to change the ownership of a file or directory. It stands for "change owner" and is a powerful tool for managing file permissions and access control.

Here's a more detailed explanation of the chown command:

Functionality:
The chown command allows you to change the user and/or group ownership of a file or directory. This is important because file ownership determines who has access to the file and what operations they can perform on it.

Syntax:
The basic syntax for the chown command is as follows:

css
Copiar
chown [options] owner[:group] file_or_directory
owner: The new user owner of the file or directory.
group: The new group owner of the file or directory (optional).
file_or_directory: The file or directory whose ownership needs to be changed.
Options:
The chown command supports several options that can modify its behavior:

-R: Recursively change the ownership of files and directories inside a directory.
-c: Display a message for each file whose ownership is changed.
-h: Change the ownership of a symbolic link itself, rather than the file or directory it points to.
-v: Display verbose output, showing the files whose ownership is changed.
--reference=RFILE: Use the owner and group of the RFILE as the reference.
Examples:

Change the owner of a file:

bash
Copiar
chown user1 file.txt
This changes the owner of file.txt to the user user1.

Change the owner and group of a file:

bash
Copiar
chown user1:group1 file.txt
This changes the owner to user1 and the group to group1 for file.txt.

Recursively change the ownership of a directory and its contents:

bash
Copiar
chown -R user1:group1 /path/to/directory
This changes the owner to user1 and the group to group1 for the directory /path/to/directory and all its files and subdirectories.

Change the ownership of a symbolic link:

bash
Copiar
chown -h user1 symlink.txt
This changes the owner of the symbolic link symlink.txt to user1, without affecting the ownership of the file it points to.

Importance:
Proper file ownership management is crucial in Linux systems, as it determines the access and permissions for different users and groups. The chown command allows system administrators and users to effectively control who can access and modify files and directories, which is essential for maintaining system security and data integrity.

By understanding and using the chown command effectively, you can ensure that your Linux system's files and directories have the appropriate ownership, which is a key aspect of file and directory permissions management.