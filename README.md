# Docker: Compreendendo e utilizando

https://www.udemy.com/docker-compreendendo-e-utilizando

Este curso tem como objetivo capacitar o aluno a entender a diferença entre Container X Virtualização, prós e contras dessas tecnologias, iniciar seu aprendizado em Docker, implementar Docker (infraestrutura de container) em seu dia a dia. E mais ... Integração com outros sistemas, topicos avançados e tudo que você procura saber sobre Docker.

## <a name="indice">Índice</a>

1. [Bem vindo](#parte1)     
2. [Introdução ao modulo](#parte2)     
3. [Conteiner ou Virtualização](#parte3)     
4. [Entendendo o Docker - Parte 1](#parte4)     
5. [Entendendo o Docker - Parte 2](#parte5)     
6. [Entendendo o Docker - Parte 3](#parte6)     
7. [Introdução ao modulo](#parte7)     
8. [Instalação e configuração do Docker](#parte8)     
9. [Introdução pratica ao Docker - Parte 1](#parte9)     
10. [Introdução pratica ao Docker - Parte 2](#parte10)     
11. [Introdução pratica ao Docker - Parte 3](#parte11)     
12. [Introdução pratica a Containers - Revisão, novas operações e interações](#parte12)     
13. [Privilegiando containers](#parte13)     
14. [Descartando containers](#parte14)     
15. [Trabalhando com variáveis de ambiente](#parte15)     
16. [Trabalhando com mapeamento de portas - Parte 1](#parte16)     
17. [Trabalhando com mapeamento de portas - Parte 2](#parte17)     
18. [Trabalhando com volumes - Parte 1](#parte18)     
19. [Trabalhando com volumes - Parte 2](#parte19)     
20. [Linkando containers - Parte 1](#parte20)     
21. [Linkando containers - Parte 2](#parte21)     
22. [Inspecionando containers](#parte22)     
23. [Exportando e Importando](#parte23)     
24. [Introdução pratica a imagens](#parte24)     
25. [Versionando imagens - Parte 1](#parte25)     
26. [Versionando imagens - Parte 2](#parte26)     
27. [Exportando e Importando](#parte27)     
28. [Entendendo o arquivo Dockerfile](#parte28)     
29. [Construindo aplicação pelo arquivo Dockerfile](#parte29)     
30. [Construindo aplicação SSH com Dockerfile](#parte30)     
31. [Introdução ao modulo](#parte31)     
32. [Introdução ao modulo](#parte32)     
33. [Parabéns](#parte33)     
---

## <a name="parte1">1 - Bem vindo</a>


[Voltar ao Índice](#indice)

---


## <a name="parte2">2 - Introdução ao modulo</a>



[Voltar ao Índice](#indice)

---


## <a name="parte3">3 - Conteiner ou Virtualização</a>


### virtualização
Em computação, virtualização é a simulação de uma plataforma de hardware, sistema operacional, dispositivo de armazenamento ou recursos de rede. 
Cada vez mais empresas estão buscando formas de reduzir os custos e complexidade com o ambiente de TI.  
A virtualização se tornou um componente chave para o desenvolvimento de uma estratégia eficiente na busca destes objetivos.  

![](img/virtualizacao_1.jpg)

Alguns detalhes importantes:
- O conceito vem da antiga !
- Hipervisor é a camada de administração da virtualização
- Existe alguns tipos de virtualização, exemplo: Full Virtualização, Para-Virtualização
- Alguns exemplos de software/plataforma/hipervisor: Xen, Citrix XenServer, VirtualBox, VMWare

### CONTAINER
Um container é uma forma de virtualização no nível do sistema operacional, um ambiente totalmente isolado, simulando um sistema independente no mesmo host.  
Com isso, é possível executar uma aplicação com todas as configurações necessárias(variáveis de ambiente, pacotes etc.) com o mínimo de impacto.

Alguns exemplos: FreeBSD Jails, OpenVZ, Outros ... LXC e Docker ...

### LXC: cgroups, namespace

#### cgroups
CGroups é uma feature do Kernel que provê mecanismos para organização de Processos em forma de grupos e limita recursos de máquina como: Consumo de CPU, memória e I/O.

#### namespace

Namespace é uma feature que permite o sistema criar diversos contextos diferentes em um mesmo sistema, ou seja, permite criar diferentes ambientes independentes que são executados no sistema base.

Com namespace eu consigo isolar um processo do ambiente de outro processo permitindo até mesmo que dois ou mais processos possuam o mesmo PID, porém em ambientes isolados. Permite que um sistema possua múltiplas visões, ou seja, que o sistema seja observado de diversas maneiras diferentes.

- https://www.opencontainers.org/ (Padronização, Investimentos)

![](img/virtualizacao_2.jpg)


[Voltar ao Índice](#indice)

---

## <a name="parte4">4 - Entendendo o Docker - Parte 1</a>

#### MERCADO x DOCKER

![](img/virtualizacao_2_3.jpg)

[Voltar ao Índice](#indice)

---

## <a name="parte5">5 - Entendendo o Docker - Parte 2</a>

#### PORQUE DOCKER ?

Porque com Docker você alcança a agilidade e controle das operações de TI construindo e executando qualquer aplicativo, em qualquer lugar!

Leve:  Containers compartilham o mesmo kernel do host logo faz uso mais eficiente dos recursos do sistema dendo um overhead menor que maquina virtual e com seu sistema de "layers" reaproveita grande parte dos dados, logo deixa downloads e armazenamento bem mais eficiente

Seguro: Containers isolam aplicativos uns dos outros e da própria infra-estrutura fornecendo uma camada adicional de proteção

Agiliza processos:  Com seus recursos de construção, herança, versionamento em segundos vocês realiza deploy da sua aplicações (ou aplicações) de forma inteligente e eficaz

Elimina inconsistência:  Como Docker empacota tudo (o sistema, libs, dependências, configuração) dentro do recipiente é possível trabalhar no ambiente de desenvolvimento, da mesma forma que o de produção, é entrega-lo exatamente como deve estar

Torna suas aplicações portáveis e padronizada:  Com os recursos Dockerfile, Dockerhub ou mesmo repositório git's em questão de segundos você distribuído (ou porta) sua aplicação de forma padronizada e documentada

O que mais: Link's entre containers, mapeamento de porta, restrição de recursos, deploy de ambiente (compose), gestão de volumes, descarte ao final --rm), Registry v2, Dockerhub etc ... Bem alguns termos: isolamento, segurança, produtividade, agilidade, INTELIGENCIA...

#### ESTRUTURA

Componentes:

- **Docker Engine/server:**  É o “Docker” propriamente dito. Ele é instalado nos Hosts e efetua a criação e a execução dos Containers de aplicações.
- **Docker Client/cli:**  É o componente onde o administrador emite os comandos que serão enviados para o Docker Engine (server).
- **Docker Hub:** É um repositório de imagens dos Containers. Basta criar uma conta e começar a usá-lo nos projetos.

Recursos/Funções:

- **Containers:**  Containers são criados a partir das imagens do Dockere eles são as instâncias reais de nossos containers. Eles podem ser iniciados, executados, parados, deletados, e movidos.
- **Imagens:**  Uma imagem nada mais é do que um ambiente totalmente encapsulado e pronto para ser replicado onde desejar.
- **Build (Dockerfiles):** Dockerfile nada mais é do que um arquivo de definição onde é possível realizar ou preparar todo ambiente a partir de um script de execução.
- **Volumes de dados:**  É uma função para realizarmos a persistência de dados uma vez que containers são projetados para descarta-lo após seu uso.
- **Mapeamento de Porta:**  Por padrão Docker não exporta suas portas para o mundo real, Mapeamento de dados é a função para expor essas portas no host 
- **Link entre container:**  Links são a funções de um container se comunicar diretamente com outro sem a necessidade de expo-lo para a rede real.

[Voltar ao Índice](#indice)

---

## <a name="parte6">6 - Entendendo o Docker - Parte 3</a>

#### Filesystem Multilayer

1. bootfs: Onde ficam o sistema de Boot do sistema e o Kernel.
2. rootfs (read only):  Inclui o sistema de arquivo do sistema, incluindo a arquitetura de diretório, em sistemas unix-like: /dev, /proc, /bin, /etc, /lib, /usr, e /tmp assim como os arquivos de configuração e binários do sistema.
3. rootfs (read/write)

![](img/virtualizacao_2_4.jpg)

- Docker machine: É um componente para automatizar a criação dos hostspara o provisionamento de containers.
- Docker Swarm: é usado para a criação dos clusters dos Hosts Docker.
- Docker compose: É usado para definir as aplicações multi-container.

[Voltar ao Índice](#indice)

---

## <a name="parte7">7 - Introdução ao modulo</a>

- Nativo apenas em LINUX
- Mac OS X
- Windows

![](img/virtualizacao_3_1.jpg)

AMBIENTE DO CURSO:

- VirtualBox 5.0.10 <https://www.virtualbox.org/>
- Ubuntu 14.04 Server
- Docker 1.9

<https://docs.docker.com/>

[Voltar ao Índice](#indice)

---

## <a name="parte8">8 - Instalação e configuração do Docker</a>

- https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository


- Material Curso: 

```
# Preparando o ambientE

sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
sudo echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > /etc/apt/sources.list.d/docker.list

sudo apt-get update
sudo apt-get purge lxc-docker
sudo apt-cache policy docker-engine

sudo apt-get install linux-image-extra-$(uname -r)

# Instalando

sudo apt-get install docker-engine
sudo service docker start

# Testando

sudo docker info
sudo docker run hello-world

```

Realizado:

[DESCOMPLICANDO O DOCKER V1 - 05 - Instalando o Docker](https://www.youtube.com/watch?v=FTxBa7i8VMM)

```
$ sudo docker info
[sudo] password for josemalcher:
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 18.09.0
Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: c4446665cb9c30056f4998ed953e6d4ff22c7c39
runc version: 4fc53a81fb7c994640722ac585fa9ca548971871
init version: fec3683
Security Options:
 apparmor
 seccomp
  Profile: default
Kernel Version: 4.15.0-43-generic
Operating System: Ubuntu 18.04.1 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 1.923GiB
Name: serverubuntu
ID: #########################################(apagado)
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
Labels:
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
Product License: Community Engine

WARNING: No swap limit support
```

**docker run hello-world**

```
root@serverubuntu:/home/josemalcher# docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
d1725b59e92d: Pull complete
Digest: sha256:b3a26e22bf55e4a5232b391281fc1673f18462b75cdc76aa103e6d3a2bce5e77
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```




[Voltar ao Índice](#indice)

---


## <a name="parte9">9 - Introdução pratica ao Docker - Parte 1</a>



[Voltar ao Índice](#indice)

---


## <a name="parte10">10 - Introdução pratica ao Docker - Parte 2</a>



[Voltar ao Índice](#indice)

---


## <a name="parte11">11 - Introdução pratica ao Docker - Parte 3</a>



[Voltar ao Índice](#indice)

---


## <a name="parte12">12 - Introdução pratica a Containers - Revisão, novas operações e interações</a>



[Voltar ao Índice](#indice)

---


## <a name="parte13">13 - Privilegiando containers</a>



[Voltar ao Índice](#indice)

---


## <a name="parte14">14 - Descartando containers</a>



[Voltar ao Índice](#indice)

---


## <a name="parte15">15 - Trabalhando com variáveis de ambiente</a>



[Voltar ao Índice](#indice)

---


## <a name="parte16">16 - Trabalhando com mapeamento de portas - Parte 1</a>



[Voltar ao Índice](#indice)

---


## <a name="parte17">17 - Trabalhando com mapeamento de portas - Parte 2</a>



[Voltar ao Índice](#indice)

---


## <a name="parte18">18 - Trabalhando com volumes - Parte 1</a>



[Voltar ao Índice](#indice)

---


## <a name="parte19">19 - Trabalhando com volumes - Parte 2</a>



[Voltar ao Índice](#indice)

---


## <a name="parte20">20 - Linkando containers - Parte 1</a>



[Voltar ao Índice](#indice)

---


## <a name="parte21">21 - Linkando containers - Parte 2</a>



[Voltar ao Índice](#indice)

---


## <a name="parte22">22 - Inspecionando containers</a>



[Voltar ao Índice](#indice)

---


## <a name="parte23">23 - Exportando e Importando</a>



[Voltar ao Índice](#indice)

---


## <a name="parte24">24 - Introdução pratica a imagens</a>



[Voltar ao Índice](#indice)

---


## <a name="parte25">25 - Versionando imagens - Parte 1</a>



[Voltar ao Índice](#indice)

---


## <a name="parte26">26 - Versionando imagens - Parte 2</a>



[Voltar ao Índice](#indice)

---


## <a name="parte27">27 - Exportando e Importando</a>



[Voltar ao Índice](#indice)

---


## <a name="parte28">28 - Entendendo o arquivo Dockerfile</a>



[Voltar ao Índice](#indice)

---


## <a name="parte29">29 - Construindo aplicação pelo arquivo Dockerfile</a>



[Voltar ao Índice](#indice)

---


## <a name="parte30">30 - Construindo aplicação SSH com Dockerfile</a>



[Voltar ao Índice](#indice)

---


## <a name="parte31">31 - Introdução ao modulo</a>



[Voltar ao Índice](#indice)

---


## <a name="parte32">32 - Introdução ao modulo</a>



[Voltar ao Índice](#indice)

---


## <a name="parte33">33 - Parabéns</a>



[Voltar ao Índice](#indice)

---

