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

Comandos:

- docker ps

```
# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

- docker ps -a

```
# docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                  PORTS               NAMES
e2fa1d02a838        hello-world         "/hello"            2 days ago          Exited (0) 2 days ago                       gallant_banzai
```

- doker help ps

```
#docker help ps

Usage:  docker ps [OPTIONS]

List containers

Options:
  -a, --all             Show all containers (default shows just running)
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print containers using a Go template
  -n, --last int        Show n last created containers (includes all states) (default -1)
  -l, --latest          Show the latest created container (includes all states)
      --no-trunc        Don't truncate output
  -q, --quiet           Only display numeric IDs
  -s, --size            Display total file sizes

```

- docker run --name exemplo1 -d -t ubuntu

```
# docker run --name exemplo1 -d -t ubuntu
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
84ed7d2f608f: Pull complete
be2bf1c4a48d: Pull complete
a5bdc6303093: Pull complete
e9055237d68d: Pull complete
Digest: sha256:868fd30a0e47b8d8ac485df174795b5e2fe8a6c8f056cc707b232d65b8a1ab68
Status: Downloaded newer image for ubuntu:latest
6ce308ac8ac03f9e145b88de8d21391e8e31b559bc612a16f12c70db0993a547

# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
6ce308ac8ac0        ubuntu              "/bin/bash"         47 seconds ago      Up 43 seconds                           exemplo1

```

- docker run --name exemplo2 -i -t ubuntu /bin/bash

```
# docker run --name exemplo2 -i -t ubuntu /bin/bash
root@ac5245980fee:/#

# exit
exit
root@serverubuntu:/home/josemalcher#
```

- Crtl + p q

```
# docker run --name exemplo3 -i -t ubuntu /bin/bash
root@f040d3353ccc:/#  # root@serverubuntu:/home/josemalcher# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS               NAMES
f040d3353ccc        ubuntu              "/bin/bash"         About a minute ago   Up About a minute                       exemplo3
6ce308ac8ac0        ubuntu              "/bin/bash"         11 minutes ago       Up 11 minutes                           exemplo1
```

- docker exec -i -t exemplo3 bash

```
# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
f040d3353ccc        ubuntu              "/bin/bash"         5 minutes ago       Up 4 minutes                            exemplo3
6ce308ac8ac0        ubuntu              "/bin/bash"         15 minutes ago      Up 14 minutes                           exemplo1

root@serverubuntu:/home/josemalcher# docker exec -i -t exemplo3 bash
root@f040d3353ccc:/#

# docker exec -i -t exemplo3 ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  18508  3152 pts/0    Ss+  00:19   0:00 /bin/bash
root        20  0.2  0.1  18508  3412 pts/1    Ss+  00:29   0:00 bash
root        30  0.0  0.1  34400  2868 pts/2    Rs+  00:29   0:00 ps aux
root@serverubuntu:/home/josemalcher# docker exec -i -t exemplo3 bash

root@f040d3353ccc:/#
root@serverubuntu:/home/josemalcher# docker exec -i -t exemplo3 ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  18508  3152 pts/0    Ss+  00:19   0:00 /bin/bash
root        20  0.1  0.1  18508  3412 pts/1    Ss+  00:29   0:00 bash
root        35  0.7  0.1  18508  3116 pts/2    Ss+  00:29   0:00 bash
root        44  0.0  0.1  34400  2960 pts/3    Rs+  00:30   0:00 ps aux
```

- docker exec exemplo3 kill -TERM 35

```
# docker exec -i -t exemplo3 ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  18508  3152 pts/0    Ss+  00:19   0:00 /bin/bash
root        20  0.1  0.1  18508  3412 pts/1    Ss+  00:29   0:00 bash
root        35  0.7  0.1  18508  3116 pts/2    Ss+  00:29   0:00 bash
root        44  0.0  0.1  34400  2960 pts/3    Rs+  00:30   0:00 ps aux

root@serverubuntu:/home/josemalcher# docker exec exemplo3 kill -TERM 35

root@serverubuntu:/home/josemalcher# docker exec -i -t exemplo3 ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  18508  3152 pts/0    Ss+  00:19   0:00 /bin/bash
root        20  0.0  0.1  18508  3412 pts/1    Ss+  00:29   0:00 bash
root        54  7.0  0.1  34400  2868 pts/2    Rs+  00:31   0:00 ps aux
root@serverubuntu:/home/josemalcher#
```

[Voltar ao Índice](#indice)

---


## <a name="parte10">10 - Introdução pratica ao Docker - Parte 2</a>

- docker stop exemplo5

```
 docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
ffe6225387b2        ubuntu              "/bin/bash"         11 seconds ago      Up 9 seconds                            exemplo5
f3014608eb41        ubuntu              "/bin/bash"         34 seconds ago      Up 31 seconds                           exemplo4
root@serverubuntu:/home/josemalcher# docker stop exemplo5
exemplo5
root@serverubuntu:/home/josemalcher# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS               NAMES
f3014608eb41        ubuntu              "/bin/bash"         About a minute ago   Up About a minute                       exemplo4
```

- docker start exemplo5

```
 docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
ffe6225387b2        ubuntu              "/bin/bash"         2 minutes ago       Exited (0) 2 minutes ago                       exemplo5
f3014608eb41        ubuntu              "/bin/bash"         3 minutes ago       Up 2 minutes                                   exemplo4
f040d3353ccc        ubuntu              "/bin/bash"         36 hours ago        Exited (0) 9 hours ago                         exemplo3
ac5245980fee        ubuntu              "/bin/bash"         36 hours ago        Exited (0) 36 hours ago                        exemplo2
6ce308ac8ac0        ubuntu              "/bin/bash"         36 hours ago        Exited (0) 9 hours ago                         exemplo1
e2fa1d02a838        hello-world         "/hello"            3 days ago          Exited (0) 3 days ago                          gallant_banzai
root@serverubuntu:/home/josemalcher# docker start exemplo5
exemplo5
root@serverubuntu:/home/josemalcher# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
ffe6225387b2        ubuntu              "/bin/bash"         3 minutes ago       Up 3 seconds                            exemplo5
f3014608eb41        ubuntu              "/bin/bash"         3 minutes ago       Up 3 minutes                            exemplo4
```

- docker images

```
# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              1d9c17228a9e        6 days ago          86.7MB
hello-world         latest              4ab4c602aa5e        3 months ago        1.84kB
```

- docker pull ubuntu:14.04

```
# docker pull ubuntu:14.04
14.04: Pulling from library/ubuntu
9b316e271c60: Pull complete
dea703e2e1f1: Pull complete
dd50fddc64ae: Pull complete
9d32d2e6dcde: Pull complete
Digest: sha256:2ceb8f8fef6dfa7433c992efdedc90c35b572747f34d9bac726e18a9e086e95e
Status: Downloaded newer image for ubuntu:14.04

root@serverubuntu:/home/josemalcher# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              14.04               7e4b16ae8b23        6 days ago          188MB
ubuntu              latest              1d9c17228a9e        6 days ago          86.7MB
hello-world         latest              4ab4c602aa5e        3 months ago        1.84kB
```

- docker run --name exemplo6 -d -t -p 80:80 nginx

```
 # docker run --name exemplo6 -d -t -p 80:80 nginx
c5c75f48167d645330f1e704d4d4880e58c87c0837def6baae4e47c924be92e0

# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
c5c75f48167d        nginx               "nginx -g 'daemon of…"   2 minutes ago       Up About a minute   0.0.0.0:80->80/tcp   exemplo6
ffe6225387b2        ubuntu              "/bin/bash"              7 hours ago         Up 7 hours                               exemplo5
f3014608eb41        ubuntu              "/bin/bash"              7 hours ago         Up 7 hours                               exemplo4
```

- docker rm exemplo1

```
r# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
root@serverubuntu:/home/josemalcher# docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                          PORTS               NAMES
c5c75f48167d        nginx               "nginx -g 'daemon of…"   12 minutes ago      Exited (0) About a minute ago                       exemplo6
ffe6225387b2        ubuntu              "/bin/bash"              7 hours ago         Exited (0) About a minute ago                       exemplo5
f3014608eb41        ubuntu              "/bin/bash"              7 hours ago         Exited (0) About a minute ago                       exemplo4
f040d3353ccc        ubuntu              "/bin/bash"              43 hours ago        Exited (0) 15 hours ago                             exemplo3
ac5245980fee        ubuntu              "/bin/bash"              43 hours ago        Exited (0) 43 hours ago                             exemplo2
6ce308ac8ac0        ubuntu              "/bin/bash"              43 hours ago        Exited (0) 15 hours ago                             exemplo1
e2fa1d02a838        hello-world         "/hello"                 3 days ago          Exited (0) 3 days ago                               gallant_banzai
root@serverubuntu:/home/josemalcher# docker rm exemplo1
exemplo1
root@serverubuntu:/home/josemalcher# docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                          PORTS               NAMES
c5c75f48167d        nginx               "nginx -g 'daemon of…"   13 minutes ago      Exited (0) About a minute ago                       exemplo6
ffe6225387b2        ubuntu              "/bin/bash"              7 hours ago         Exited (0) About a minute ago                       exemplo5
f3014608eb41        ubuntu              "/bin/bash"              7 hours ago         Exited (0) About a minute ago                       exemplo4
f040d3353ccc        ubuntu              "/bin/bash"              43 hours ago        Exited (0) 15 hours ago                             exemplo3
ac5245980fee        ubuntu              "/bin/bash"              43 hours ago        Exited (0) 43 hours ago                             exemplo2
e2fa1d02a838        hello-world         "/hello"                 3 days ago          Exited (0) 3 days ago                               gallant_banzai
```

- docker rmi ubuntu:14.04

```
# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              7042885a156a        6 days ago          109MB
ubuntu              14.04               7e4b16ae8b23        6 days ago          188MB
ubuntu              latest              1d9c17228a9e        6 days ago          86.7MB
hello-world         latest              4ab4c602aa5e        3 months ago        1.84kB
root@serverubuntu:/home/josemalcher# docker rmi ubuntu:14.04
Untagged: ubuntu:14.04
Untagged: ubuntu@sha256:2ceb8f8fef6dfa7433c992efdedc90c35b572747f34d9bac726e18a9e086e95e
Deleted: sha256:7e4b16ae8b23e239ab03a413febb51e204e294cb2bf0e45cc4aa7bed7d7f704e
Deleted: sha256:31fee1a1223e18212fbfabdbc6c1d858539736e72ebc6e5656b5bbe1a6a3e6f0
Deleted: sha256:46eadf76580d8e4b62992ec2a5ad6fbe665a2315e249dae0f93b79137694b6bf
Deleted: sha256:e41a350db85f18619768eadfb3b8e4e72e07318486614a5acf708fdd45781c4c
Deleted: sha256:a1dfb45ac02d4300506f63948d1a9d1bc9e354d0643412e6b88cc9dec820216f
root@serverubuntu:/home/josemalcher# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              7042885a156a        6 days ago          109MB
ubuntu              latest              1d9c17228a9e        6 days ago          86.7MB
hello-world         latest              4ab4c602aa5e        3 months ago        1.84kB
```


[Voltar ao Índice](#indice)

---


## <a name="parte11">11 - Introdução pratica ao Docker - Parte 3</a>

- \Exemplo5\Dockerfile
- docker build -t nginx-exemplo:v2 .

```
# docker build -t nginx-exemplo:v2 .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM nginx
 ---> 7042885a156a
Step 2/3 : RUN sed -i 's/Welcome to nginx!/Bem vindo  ao exemplo 5 <br> Via Dockerfile/g' /usr/share/nginx/html/index.html
 ---> Using cache
 ---> b398a10ef777
Step 3/3 : RUN ls '/tmp'
 ---> Running in ffb671cb4939
Removing intermediate container ffb671cb4939
 ---> 653db82a75fd
Successfully built 653db82a75fd
Successfully tagged nginx-exemplo:v2

# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx-exemplo       v2                  653db82a75fd        6 seconds ago       109MB
nginx-exemplo1      v1                  b398a10ef777        5 minutes ago       109MB
nginx               latest              7042885a156a        6 days ago          109MB
ubuntu              latest              1d9c17228a9e        6 days ago          86.7MB
hello-world         latest              4ab4c602aa5e        3 months ago        1.84kB
```

-  docker run --name exemplo51 -d -t -p 80:80 nginx-exemplo:v2

```
# docker run --name exemplo51 -d -t -p 80:80 nginx-exemplo:v2
920d626b272026462879e3bd5de93bd7b89c7556e625a29a55e9672204f6a9bd
root@serverubuntu:/home/josemalcher/exemplo5# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
920d626b2720        nginx-exemplo:v2    "nginx -g 'daemon of…"   5 seconds ago       Up 4 seconds        0.0.0.0:80->80/tcp   exemplo51
```

[Voltar ao Índice](#indice)

---


## <a name="parte12">12 - Introdução pratica a Containers - Revisão, novas operações e interações</a>

- docker restart exemplo6
- docker pause exemplo6
- docker unpause exemplo6
- docker kill exemplo6
- docker attach exemplo6 (ctrl + p +q)

copiar aqrquivos para container:

- docker cp exemplo6:/tmp/arquivos1 ./ (copiar container ex6 para pasta local ./)

Nomear hostname

- docker run -it --name exemplo6.c --hostname exemplo6host ubuntu /bin/bash

```
# docker run -it --name exemplo6.b ubuntu /bin/bash
root@91bd5885378f:/#
root@91bd5885378f:/# exit
exit

root@serverubuntu:/home/josemalcher# docker run -it --name exemplo6.c --hostname exemplo6host ubuntu /bin/bash
root@exemplo6host:/#
```

[Voltar ao Índice](#indice)

---


## <a name="parte13">13 - Privilegiando containers</a>

Baixando img
- docker pull andyshinn/dnsmasq

Privilégio total:
- docker run -dt --name exemplo7 --privileged andyshinn/dnsmasq

Específico: (placa de rede)
- docker run -dt --name exemplo7 --cap-add=NET_ADMIN andyshinn/dnsmasq

[Voltar ao Índice](#indice)

---


## <a name="parte14">14 - Descartando containers</a>

Script bash para ficar verificando o status docker:

```bash
function docker.ps.loop(){
    watch -n 3 -t "docker ps --format '{{.Names}},{{.Image}}\n{{.Status}}, PORTA: {{.Ports}}\n'"
}
```

**Recarregar o Bash: # source ~/.bashrc**

- docker run -it --rm --name exemplo8 --hostname exempli8 -p 80:80 -v /home/josemalcher/exemplo8/index.html:/usr/share/nginx/html/index.html nginx-exemplo1:v1

"--rm" descarta o container ao sair.

```
docker run -i --rm --name exemplo8 --hostname exempli8 -p 80:80 -v /home/josemalcher/exemplo8/index.html:/usr/share/nginx/html/index.html nginx-exemplo1:v1

exemplo8,nginx-exemplo1:v1
Up 45 seconds, PORTAS: 0.0.0.0:80->80/tcp
```

[Voltar ao Índice](#indice)

---


## <a name="parte15">15 - Trabalhando com variáveis de ambiente</a>

- https://hub.docker.com/r/sameersbn/mysql

- v=A0502E01 ; docker run -it --rm --name $v --hostname $v -e 'X=varival1' --env='Y=variavel2' ubuntu /bin/bash

```
# v=A0502E01 ; docker run -it --rm --name $v --hostname $v -e 'X=varival1' --env='Y=variavel2' ubuntu /bin/bash

root@A0502E01:/# echo "Imprimindo valor de X: $X, Y:$Y e Z:$Z"
Imprimindo valor de X: varival1, Y:variavel2 e Z:

```

- v=A0502E02 ; docker run -it --rm --name $v --hostname $v -e 'DB_NAME=db' -e 'DB_USER=user1' -e 'DB_PASS=123' sameersbn/mysql

```
# v=A0502E02 ; docker run -it --rm --name $v --hostname $v -e 'DB_NAME=db' -e 'DB_USER=user1' -e 'DB_PASS=123' sameersbn/mysql
Installing database...
Starting MySQL server...
Waiting for database server to accept connections.
Creating debian-sys-maint user...
Creating database "db"...
Granting access to database "db" for user "user1"...
2019-01-06T21:41:37.379842Z mysqld_safe Logging to syslog.
2019-01-06T21:41:37.428114Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

# docker exec -it A0502E02 mysql -u user1 --password=123

mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.7.22-0ubuntu18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| db                 |
+--------------------+
2 rows in set (0.00 sec)

mysql>
```

**Variáveis dentro de arquivos**

```
# v=A0502E03 ; docker run -it --rm --name $v --hostname $v --env-file=/home/josemalcher/exemplo9/variaveisDB sameersbn/mysql
Installing database...
Starting MySQL server...
Waiting for database server to accept connections.
Creating debian-sys-maint user...
Creating database "db_arquivovar"...
Granting access to database "db_arquivovar" for user "user2"...
2019-01-06T21:51:46.178424Z mysqld_safe Logging to syslog.
2019-01-06T21:51:46.220244Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

# docker exec -it A0502E03 mysql -u user2 --password=12356
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1045 (28000): Access denied for user 'user2'@'localhost' (using password: YES)

# docker exec -it A0502E03 mysql -u user2 --password=123456
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.7.22-0ubuntu18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| db_arquivovar      |
+--------------------+
2 rows in set (0.00 sec)

```


[Voltar ao Índice](#indice)

---

## <a name="parte16">16 - Trabalhando com mapeamento de portas - Parte 1</a>

```
    # docker run -dt --name aulaEx1-a ubuntu /bin/bash

    # docker run -dt --name aulaEx1-b -p 8080:80 ubuntu /bin/bash


aulaEx1-b,ubuntu
Up 59 seconds, PORTA: 0.0.0.0:8080->80/tcp

aulaEx1-a,ubuntu
Up About a minute, PORTA:
```

```
    # docker port aulaEx1-b
    80/tcp -> 0.0.0.0:8080
```

Mapeamento mais de uma porta

```
# docker run -dt --name aulaEx3-a -p 23:23 -p 81-85:81-85 ubuntu /bin/bash

aulaEx3-a,ubuntu
Up 15 seconds, PORTA: 0.0.0.0:23->23/tcp, 0.0.0.0:81-85->81-85/tcp
```

Determinar ip de restrição

```
# docker run -dt --name aulaEx3-b -p 192.168.0.102:24:24 ubuntu /bin/bash

aulaEx3-b,ubuntu
Up 25 seconds, PORTA: 192.168.0.102:24->24/tcp

```

Redirecionar para porta udp

```
# docker run -dt --name aulaEx3-c -p 54:54/udp ubuntu /bin/bash

aulaEx3-c,ubuntu
Up 21 seconds, PORTA: 0.0.0.0:54->54/udp
```

Exemplo de muitas portas

```
# docker run -dt --name aulaEx5-d -p 54-55:54-55/udp -p 192.168.0.102:100:101/tcp -p 86-89:96-99 ubuntu /bin/bash

aulaEx5-d,ubuntu
Up 19 seconds, PORTA: 0.0.0.0:54-55->54-55/udp, 0.0.0.0:86->96/tcp, 0.0.0.0:87->97/tcp, 0.0.0.0:88->98/tcp, 0.0.0.0:89->99/tcp, 192.168.0.102:100->1
01/tcp

```


[Voltar ao Índice](#indice)

---


## <a name="parte17">17 - Trabalhando com mapeamento de portas - Parte 2</a>

```
# docker run -dt --name Aula17.a -P nginx

Aula17.a,nginx
Up 18 seconds, PORTA: 0.0.0.0:32768->80/tcp
```


[Voltar ao Índice](#indice)

---


## <a name="parte18">18 - Trabalhando com volumes - Parte 1</a>

```

# docker run -it --rm --name Aula18Ex1 
  -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1:/tmp/Ex01:Z ubuntu /bin/bash

```

- ":Z" Parâmetro aidiconado: http://www.projectatomic.io/blog/2015/06/using-volumes-with-docker-can-cause-problems-with-selinux/
- ":ro" Ready only - Somente para leitura

```
# docker run -it --rm --name Aula18Ex3 
-v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1/Exemplo1:/home/Exemplo1:Z 
-v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1/Exemplo2:/home/Exemplo2:Z ubuntu /bin/bash
```

Prática com Mysql

```
# docker run -i --rm --name Aula18Ex4 -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1/ArquivosBD/:/var/lib/mysql:Z -e 'DB_NAME=db1' -e 'DB_USER=user1' -e 'DB_PASS=123' sameersbn/mysqlInstalling database...

Starting MySQL server...
Waiting for database server to accept connections.
Creating debian-sys-maint user...
Creating database "db1"...
Granting access to database "db1" for user "user1"...
2019-05-03T00:40:55.157354Z mysqld_safe Logging to syslog.
2019-05-03T00:40:55.174405Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

Aula18Ex4,sameersbn/mysql
Up 31 seconds, PORTA: 3306/tcp

[ArquivosBD] # ls

auto.cnf  db1  ib_buffer_pool  ibdata1  ib_logfile0  ib_logfile1  ibtmp1  mysql  performance_schema  sys

# docker exec -it Aula18Ex4 mysql -u user1 --password=123

mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.24-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| db1                |
+--------------------+
2 rows in set (0.00 sec)

mysql> 

```

Exemplo 2 - Adicionando outro Banco

```
# docker run -i --rm --name Aula18Ex5 -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1/ArquivosBD/:/var/lib/mysql:Z -e 'DB_NAME=db2' -e 'DB_USER=user1' -e 'DB_PASS=123' sameersbn/mysqlCreating database "db2"...
Granting access to database "db2" for user "user1"...
2019-05-03T00:47:03.870862Z mysqld_safe Logging to syslog.
2019-05-03T00:47:03.895562Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

[ArquivosBD] # ls
auto.cnf  db1  db2  ib_buffer_pool  ibdata1  ib_logfile0  ib_logfile1  ibtmp1  mysql  performance_schema  sys



# docker exec -it Aula18Ex5 mysql -u user1 --password=123

mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.24-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| db1                |
| db2                |
+--------------------+
3 rows in set (0.00 sec)

mysql> 

```

Verificação...

```
# dockerun -i --rm --name Aula18Ex4 -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/18-Trabalhando-com-volumes-Parte-1/ArquivosBD/:/var/lib/mysql:Z -e 'DB_NAME=db1' -e 'DB_USER=user1' -e 'DB_PASS=123' sameersbn/mysql
Creating database "db1"...
Granting access to database "db1" for user "user1"...
2019-05-03T00:52:16.713861Z mysqld_safe Logging to syslog.
2019-05-03T00:52:16.732779Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

# docker exec -it Aula18Ex4 mysql -u user1 --password=123
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.24-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| db1                |
| db2                |
+--------------------+
3 rows in set (0.00 sec)

mysql> 


[ArquivosBD] # ls
auto.cnf  db1  db2  ib_buffer_pool  ibdata1  ib_logfile0  ib_logfile1  ibtmp1  mysql  performance_schema  sys

```



[Voltar ao Índice](#indice)

---


## <a name="parte19">19 - Trabalhando com volumes - Parte 2</a>

```
# docker run -i --rm --name Aula19Ex1 -p 8080:80 -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/19-Trabalhando-com-volumes-Parte-2/index.html:/usr/share/nginx/html/index.html:Z nginx

Aula19Ex1,nginx
Up 38 seconds, PORTA: 0.0.0.0:8080->80/tcp

```

Espelhando os arquivos para outra container

**Adicionado "--privileged=true" para poder ter permissão aos arquivos!**

```
# docker run -dt --privileged=true --name Aula19Ex2 -p 8180:80 --volumes-from=Aula19Ex1 nginx
```


[Voltar ao Índice](#indice)

---


## <a name="parte20">20 - Linkando containers - Parte 1</a>


É necessário instalar o ping:

```
# docker exec -it Aula9-d /bin/bash
# apt-get update && apt-get install -y iputils-ping
```


```
# docker run -dt --name Aula9-a ubuntu /bin/bash

# docker run -dt --name Aula9-b --link Aula9-a  ubuntu /bin/bash

# docker run -dt --name Aula9-c  ubuntu /bin/bash

# docker exec Aula9-b ping Aula9-c -c 3
ping: Aula9-c: Temporary failure in name resolution

# docker exec Aula9-b ping Aula9-a -c 3
PING Aula9-a (172.17.0.2) 56(84) bytes of data.
64 bytes from Aula9-a (172.17.0.2): icmp_seq=1 ttl=64 time=0.097 ms
64 bytes from Aula9-a (172.17.0.2): icmp_seq=2 ttl=64 time=0.080 ms
64 bytes from Aula9-a (172.17.0.2): icmp_seq=3 ttl=64 time=0.076 ms

--- Aula9-a ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2030ms
rtt min/avg/max/mdev = 0.076/0.084/0.097/0.011 ms

```

Exemplo 2

```
# docker run -dt --name Aula9-d --link Aula9-a:l1 --link Aula9-b:l2 --link Aula9-c ubuntu /bin/bash

# docker exec Aula9-d ping l1 -c 3
PING l1 (172.17.0.2) 56(84) bytes of data.
64 bytes from l1 (172.17.0.2): icmp_seq=1 ttl=64 time=0.083 ms
64 bytes from l1 (172.17.0.2): icmp_seq=2 ttl=64 time=0.139 ms
64 bytes from l1 (172.17.0.2): icmp_seq=3 ttl=64 time=0.109 ms

--- l1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2076ms
rtt min/avg/max/mdev = 0.083/0.110/0.139/0.024 ms

# docker exec Aula9-d ping l1 -c 3
PING l1 (172.17.0.2) 56(84) bytes of data.
64 bytes from l1 (172.17.0.2): icmp_seq=1 ttl=64 time=0.083 ms
64 bytes from l1 (172.17.0.2): icmp_seq=2 ttl=64 time=0.139 ms
64 bytes from l1 (172.17.0.2): icmp_seq=3 ttl=64 time=0.109 ms

--- l1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2076ms
rtt min/avg/max/mdev = 0.083/0.110/0.139/0.024 ms

# docker exec Aula9-d ping Aula9-a -c 3
PING l1 (172.17.0.2) 56(84) bytes of data.
64 bytes from l1 (172.17.0.2): icmp_seq=1 ttl=64 time=0.056 ms
64 bytes from l1 (172.17.0.2): icmp_seq=2 ttl=64 time=0.319 ms
64 bytes from l1 (172.17.0.2): icmp_seq=3 ttl=64 time=0.135 ms

--- l1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2052ms
rtt min/avg/max/mdev = 0.056/0.170/0.319/0.110 ms

# docker exec Aula9-d ping l2 -c 3
PING l2 (172.17.0.3) 56(84) bytes of data.
64 bytes from l2 (172.17.0.3): icmp_seq=1 ttl=64 time=0.078 ms
64 bytes from l2 (172.17.0.3): icmp_seq=2 ttl=64 time=0.115 ms
64 bytes from l2 (172.17.0.3): icmp_seq=3 ttl=64 time=0.121 ms

--- l2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2056ms
rtt min/avg/max/mdev = 0.078/0.104/0.121/0.022 ms

# docker exec Aula9-d ping l3 -c 3
ping: l3: Name or service not known

# docker exec Aula9-d ping Aula9-d -c 3
ping: Aula9-d: Name or service not known

# docker exec Aula9-d ping Aula9-c -c 3
PING Aula9-c (172.17.0.4) 56(84) bytes of data.
64 bytes from Aula9-c (172.17.0.4): icmp_seq=1 ttl=64 time=0.105 ms
64 bytes from Aula9-c (172.17.0.4): icmp_seq=2 ttl=64 time=0.100 ms
64 bytes from Aula9-c (172.17.0.4): icmp_seq=3 ttl=64 time=0.129 ms

--- Aula9-c ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2063ms
rtt min/avg/max/mdev = 0.100/0.111/0.129/0.015 ms

```

[Voltar ao Índice](#indice)

---


## <a name="parte21">21 - Linkando containers - Parte 2</a>

```
# docker run -dt --name Aula21-ex2-db 
    -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/21-Linkando-containers-Parte-2/:/var/lib/mysql:Z 
    -e 'DB_NAME=redmine_base'
    -e 'DB_USER=redmine_usuario' 
    -e 'DB_PASS=redmine_senha' 
    sameersbn/mysql:latest
    
c31b360dec1ab312be29bb00a339c72417ca6fb12cad33231945561b413c4e62


#  docker ps
CONTAINER ID   IMAGE   COMMAND     CREATED    STATUS   PORTS           NAMES
c31b360dec1a   sameersbn/mysql:latest   "/sbin/entrypoint...."   3 minutes ago       Up 3 minutes        3306/tcp       Aula21-ex2-db

# docker run -i --rm --name Aula21-ex2-app -p 8080:80 
    -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/21-Linkando-containers-Parte-2-app/:/home/redmine/data:Z 
    -e 'DB_TYPE=mysql' 
    -e 'DB_HOST=redminedb' 
    -e 'DB_NAME=redmine_base' 
    -e 'DB_USER=redmine_usuario' 
    -e 'DB_PASS=redmine_senha' 
    --link Aula21-ex2-db:redminedb 
    sameersbn/redmine:3.1.1-3

Waiting for database server to accept connections
2019-05-10 22:13:41,465 CRIT Supervisor running as root (no user in config file)
2019-05-10 22:13:41,465 WARN Included extra file "/etc/supervisor/conf.d/cron.conf" during parsing
2019-05-10 22:13:41,465 WARN Included extra file "/etc/supervisor/conf.d/unicorn.conf" during parsing
2019-05-10 22:13:41,466 WARN Included extra file "/etc/supervisor/conf.d/nginx.conf" during parsing
2019-05-10 22:13:41,513 INFO RPC interface 'supervisor' initialized
2019-05-10 22:13:41,513 CRIT Server 'unix_http_server' running without any HTTP authentication checking
2019-05-10 22:13:41,514 INFO supervisord started with pid 1
2019-05-10 22:13:42,516 INFO spawned: 'unicorn' with pid 91
2019-05-10 22:13:42,517 INFO spawned: 'cron' with pid 92
2019-05-10 22:13:42,520 INFO spawned: 'nginx' with pid 93
2019-05-10 22:13:44,240 INFO success: unicorn entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2019-05-10 22:13:44,240 INFO success: cron entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2019-05-10 22:13:44,240 INFO success: nginx entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)

```

[Voltar ao Índice](#indice)

---


## <a name="parte22">22 - Inspecionando containers</a>

```
# docker run -dt --name Aula511-ex1 
    --hostname Aula511-ex1 
    -p 8080:80 -p 81:91 
    -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/511-inspecionando-containers-1/:/tmp:Z 
    ubuntu /bin/bash

```

```
# docker run -dt --name Aula511-ex1 --hostname Aula511-ex1 -p 8080:80 -p 81:91 -v /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/511-inspecionando-containers-1/:/tmp:Z ubuntu /bin/bash

# docker inspect Aula511-ex1 
[
    {
        "Id": "a5177bed824b47760bba705da3ff1a570518e82ea7fd6a1e66",
        "Created": "2019-05-11T13:03:46.3282937Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 7451,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2019-05-11T13:03:47.90327774Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:d131e0fa2585a7efbfb187f70d648aa50e251d9d3b7031edf",
        "ResolvConfPath": "/var/lib/docker/containers/a5177bed824b47760bba705da3ff1a57082ea7fd6a1e66a80975cc1cfa09/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/a5177bed824b47760bba705da3ff1a58e82ea7fd6a1e66a80975cc1cfa09/hostname",
        "HostsPath": "/var/lib/docker/containers/a5177bed824b47760bba705da3ff1a18e82ea7fd6a1e66a80975cc1cfa09/hosts",
        "LogPath": "",
        "Name": "/Aula511-ex1",

#(....muitas outras infos)

# docker inspect --format '{{.Id}}' Aula511-ex1 
a5177bed824b47760bba705da3ff1a570518e82ea7fd6a1e66a80975cc1cfa09

# docker inspect --format '{{.NetworkSettings}}' Aula511-ex1 
{{ 65b499414d26f9f70ea8dafa714754da8a994e6219cda58ed31d1278fab48aa4 false  0 map[80/tcp:[{0.0.0.0 8080}] 91/tcp:[{0.0.0.0 81}]] /var/run/docker/netns/65b499414d26 [] []} {e2f79b1d0451f9159c51c83898c20cd5f6147895c7d6fa75d2ca7783df610e92 172.17.0.1  0 172.17.0.2 16  02:42:ac:11:00:02} map[bridge:0xc00012a000]}

# docker inspect --format '{{.NetworkSettings.IPAddress}}' Aula511-ex1 
172.17.0.2


```


```

# docker inspect --format 'Inf: {{.Name}} | {{.Config.Hostname}} | {{.NetworkSettings.IPAddress}}' Aula511-ex1
Inf: /Aula511-ex1 | Aula511-ex1 | 172.17.0.2


```

**Diff**

```
# docker exec Aula511-ex1 touch /usr/src/arquivo1
# docker exec Aula511-ex1 touch /usr/src/arquivo2
# docker diff Aula511-ex1 
C /run
D /run/secrets
C /usr/src
A /usr/src/arquivo1
A /usr/src/arquivo2

# docker exec -it Aula511-ex1 bash
root@Aula511-ex1:/# touch /tmp/arquiv3
root@Aula511-ex1:/# echo "alter file">>/usr/src/arquivo2
root@Aula511-ex1:/# exit
exit

# docker diff Aula511-ex1 
C /root
A /root/.bash_history
C /run
D /run/secrets
C /usr/src
A /usr/src/arquivo1
A /usr/src/arquivo2

```

**Logs**

```
# docker run -dt --name Aula511-ex2 =p 8080:80 -p 443:443 -p 3306:3306 dell/wordpress

# docker logs Aula511-ex2


```



[Voltar ao Índice](#indice)

---


## <a name="parte23">23 - Exportando e Importando</a>

```
# docker run -dt --name Aula512 ubuntu /bin/bash
6f9257703d8f4a30ec6a882a2c60255fa1f6313c6288b20519239341f1c37038

# docker exec Aula512 touch /usr/src/arquivo-bkp-teste_1

# docker diff Aula512 
C /run
D /run/secrets
C /usr/src
A /usr/src/arquivo-bkp-teste_1

# docker export -o /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/512-exportando-importando/container-Aula512.tar Aula512

# ls 512-exportando-importando/
container-Aula512.tar

# cat 512-exportando-importando/container-Aula512.tar | docker import - aula512:v1
sha256:01d84de66f72fcd34468564fe25b6a28bd779b324359fbd45658151a3d308812

# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
aula512                            v1                  01d84de66f72        6 seconds ago       81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB


# docker run -dt --name Aula512-v1 aula512:v1 /bin/bash
73638ab1d24bfd6e863153011d0fe03d70cdedeeb4344469584cdc310dcdb85c

# docker exec Aula512-v1 ls /usr/src
arquivo-bkp-teste_1

```



[Voltar ao Índice](#indice)

---


## <a name="parte24">24 - Introdução pratica a imagens</a>

```
# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
aula512                            v1                  01d84de66f72        18 minutes ago      81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB


# docker pull ubuntu:10.04

# docker pull centos

# docker pull nginx


# docker search wordpress


```

**Base de Imagens**

- https://hub.docker.com


[Voltar ao Índice](#indice)

---


## <a name="parte25">25 - Versionando imagens - Parte 1</a>

- https://hub.docker.com


```
# docker info
Containers: 3
 Running: 0
 Paused: 0
 Stopped: 3
Images: 10
Server Version: 1.13.1
Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: true
Logging Driver: journald
Cgroup Driver: systemd
Plugins: 
 Volume: local
 Network: bridge host macvlan null overlay
 Authorization: rhel-push-plugin
Swarm: inactive

(...)

# docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: josemalcher
Password: 

#docker logout

# docker login -u josemalcher -e contato@josemalche.net
Flag --email has been deprecated, will be removed in 1.14.
Password: 


```

[Voltar ao Índice](#indice)

---


## <a name="parte26">26 - Versionando imagens - Parte 2</a>

```
# docker run -dt --name aula63 ubuntu /bin/bash
4104e4d78fc6952b7f857b8d5e9ae55b90dc315e10e399371e984aa7191bf550

# docker exec aula63 touch /usr/src/imagem-alterada

# docker diff aula63 
C /run
D /run/secrets
C /usr/src
A /usr/src/imagem-alterada

# docker commit -m "Versionando imagem - exemplo 1" aula63 aula63:v1


# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
aula63                             v1                  6a96d5d9fd50        15 seconds ago      102 MB
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB


# docker push aula63:v1
Error response from daemon: You cannot push a "root" repository. Please rename your repository to docker.io/<user>/<repo> (ex: docker.io/<user>/aula63)

# docker commit -m "Versionando imagem - exemplo 2" aula63 josemalcher/aula63:v2

# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
josemalcher/aula63                 v2                  367ead2fa1a1        7 seconds ago       102 MB
aula63                             v1                  6a96d5d9fd50        3 minutes ago       102 MB
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB


# docker push josemalcher/aula63
The push refers to a repository [docker.io/josemalcher/aula63]


# docker pull josemalcher/aula63:v2


# docker tag josemalcher/aula63:v2 josemalcher/aula63:latest

# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
josemalcher/aula63                 latest              367ead2fa1a1        4 minutes ago       102 MB
josemalcher/aula63                 v2                  367ead2fa1a1        4 minutes ago       102 MB
aula63                             v1                  6a96d5d9fd50        7 minutes ago       102 MB
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB

# docker push josemalcher/aula63

```



[Voltar ao Índice](#indice)

---


## <a name="parte27">27 - Exportando e Importando</a>

```

# docker save -o 64-exportando-importando/aula64-ex1-latest.tar josemalcher/aula63:latest 

$ ls -lha
total 100M
drwxrwxr-x.  2 josemalcher josemalcher 4,0K mai 11 21:38 .
drwxrwxr-x. 14 josemalcher josemalcher 4,0K mai 11 21:35 ..
-rw-------.  1 root        root        100M mai 11 21:38 aula64-ex1-latest.tar


# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
josemalcher/aula63                 latest              367ead2fa1a1        16 minutes ago      102 MB
josemalcher/aula63                 v2                  367ead2fa1a1        16 minutes ago      102 MB
aula63                             v1                  6a96d5d9fd50        19 minutes ago      102 MB
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB

# docker rmi -f josemalcher/aula63:latest josemalcher/aula63:v2 aula63:v1
Untagged: josemalcher/aula63:latest
Untagged: josemalcher/aula63:v2
Deleted: sha256:367ead2fa1a1ab3e593d3b1883189a591f0a72c345ae177e678ff80444e452f7
Untagged: aula63:v1
Deleted: sha256:6a96d5d9fd50382cf103ab9b49011e953b3f37ff3c7f2782e5da3d97e11096ca
Deleted: sha256:3d4be9bc1e3787c089c5b1c29fa785d9424a3f29d0e67a642c75763fb278b0de

# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB

# docker load < /home/josemalcher/Documentos/workspace-Docker/udemy-Docker-Compreendendo-e-utilizando/64-exportando-importando/aula64-ex1-latest.tar
6d4cdb9eb527: Loading layer [==================================================>] 4.096 kB/4.096 kB
Loaded image: josemalcher/aula63:latest

# docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
josemalcher/aula63                 latest              367ead2fa1a1        20 minutes ago      102 MB
aula512                            v1                  01d84de66f72        3 hours ago         81.5 MB
docker.io/ubuntu                   14.04               65613486b3ef        2 weeks ago         188 MB
docker.io/ubuntu                   latest              d131e0fa2585        2 weeks ago         102 MB
docker.io/nginx                    latest              27a188018e18        3 weeks ago         109 MB
registry.access.redhat.com/rhel7   latest              5044f6040ea5        3 weeks ago         203 MB
docker.io/sameersbn/redmine        latest              1239aa7aa1ea        4 weeks ago         816 MB
quay.io/sameersbn/mysql            latest              40df973b8e91        3 months ago        289 MB
docker.io/hello-world              latest              fce289e99eb9        4 months ago        1.84 kB
docker.io/andyshinn/dnsmasq        latest              831c17422076        13 months ago       4.88 MB
docker.io/sameersbn/redmine        3.1.1-3             9655f66d3116        3 years ago         612 MB


```


[Voltar ao Índice](#indice)

---


## <a name="parte28">28 - Entendendo o arquivo Dockerfile</a>

```
FROM ubuntu
MAINTAINER José Malcher Jr. <contato@josemalcher.net>

# Labe's
LABEL "net.josemalcher.vendor"="Udemy Course"
LABEL version="1.0"
LABEL description="Curso de Docker: \
Exemplo básico de Dockerfile."

# Variáveis
ENV DIR_BASE=/usr/src
ENV DIR_TESTE1=$DIR_BASE/teste1
ENV USER=josemalcher
ENV PASS=123456

# adiciona Arquivos
ADD arquivos/exemplos/ $DIR_BASE/exemplos
ADD arquivos/apt_defaults.pgks /tmp/apt_defaults.pgks

# Executa processos
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get -y install autoconf build-essential gcc make
RUN apt-get install -y -q $(cat /tmp/apt_defaults.pgks)

RUN locale-gen pt_BR.UTF-8
RUN update-locale LANG=pt_BR.UTF-8

#local de trabalho
WORKDIR $DIR_BASE
RUN touch exemplo_04.txt

WORKDIR $DIR_BASE/exemplos
RUN touch exemplo_05.txt

#################################################

# POSTS

EXPOSE 80
EXPOSE 81
EXPOSE 82 83


# VOLUMES
VOLUME ["/usr/src","/home"]


##################################################


# CMD
CMD ["/bin/bash"]


```

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

