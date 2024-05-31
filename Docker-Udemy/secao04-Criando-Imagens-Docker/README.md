# Criando Imagens Docker:

## O que são Imagens e Containers?:

### O que é Imagem:
- Cut-Down OS, ou seja, tem um Sistema Opperacional dentro dele

- Tem todas as bibliotecas que precisa para que a sua aplicação rode

- Tudo que a sua aplicação precisa para funcionar de arquivos estão lá dentro

- Variáveis de ambiente (enviroment variables)

- Basicamente, a definição de uma imagem em Docker seria algo que contém tudo o que vc precisa para uma aplicação funcionar

### O que é Container:
- É como se fosse uma VM de forma isolado

- Ele tem start/stop

- É um processo que roda dentro de uma máquina

### A aplicacao:
- Vamos realizar uma aplicação local iniciando tudo do zero pegando um app teste e a partir dela realizar o processo de criação da imagem e, por fim, rodar ela.

    - No Google, procure por Docker Sample Application - https://docs.docker.com/get-started/02_our_app/
    
    - No link acima, podemos realizar um download de um arquivo zipado para conseguir baixar o arquivo teste que consta com nome getting-started-master e dentro dela pegar apenas o diretório app.
