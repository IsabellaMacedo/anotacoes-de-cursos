# DESCOMPLICANDO O DOCKER (LinuxTips)


### Documentação:

Docker: https://docs.docker.com/get-started/ <br />
Livro Descomplicando o Docker: https://livro.descomplicandodocker.com.br/
Anotações das aulas, e recortes do livro.

#### Permissões das camadas:
Na construção da imagem do Docker, cada passo cria uma camada, sendo que a última a ser criada é read-write, e as demais são read-only.


<a href="https://docs.docker.com/storage/storagedriver/" target="_blank">
  <img src=https://docs.docker.com/storage/storagedriver/images/container-layers.jpg>
</a>

<a href="https://docs.docker.com/storage/storagedriver/" target="_blank">
  <img src=https://docs.docker.com/storage/storagedriver/images/sharing-layers.jpg>
</a>

- READ AND WRITE (R/W): é a última camada do container (topo), e é a que pode ser alterada;
- READ ONLY (R/O): demais camadas anteriores (imagem) que são somente leitura;
- COPY ON WRITE (CoW): para alterar uma camada read only inferior, faz o copy on write.
> " Copy-on-write is a strategy of sharing and copying files for maximum efficiency. If a file or directory exists in a lower layer within the image, 
> and another layer (including the writable layer) needs read access to it, it just uses the existing file. The first time another layer needs to modify 
> the file (when building the image or running the container), the file is copied into that layer and modified. "

* VERSÃO:
>` docker --version `

* LISTAR OS CONTAINERS:
(comando antigo era o "docker ps", ainda funciona, mas o novo é o abaixo)
>`docker container ls`

O retorno do comando acima traz:

* CONTAINER ID - Identificação única do container.
* IMAGE - A imagem que foi utilizada para a execução do container.
* COMMAND - O comando em execução.
* CREATED - Quando ele foi criado.
* STATUS - O seu status atual.
* PORTS - A porta do container e do host que esse container utiliza.
* NAMES - O nome do container.


* LISTAR TODOS OS CONTAINERS (EM EXECUÇÃO E OS MORTOS/PARADOS):
> `docker container ls -a`

* EXECUTAR O HELLO WORLD (CONFERIR SE TÁ INSTALADO CORRETAMENTE)
> `docker run hello-world`
(quando a imagem não existe, o Docker primeiro vai fazer o Pull e depois executar)


* EXECUTAR O CONTAINER E JÁ ABRIR O TERMINAL INTERATIVO
> `docker container run -ti`
(ti: terminal interativo, quando o container subir, já estará conectado no terminal à ele)

> -t -- Disponibiliza um TTY (console) para o nosso container.
> -i -- Mantém o STDIN aberto mesmo que você não esteja conectado no container.
> -d -- Faz com que o container rode como um daemon, ou seja, sem a interatividade que os outros dois parâmetros nos fornecem.

#### -ti OU -d:

se você quer subir um container para ser utilizado como uma máquina Linux convencional com shell e que necessita de alguma configuração ou ajuste, utilize o modo interativo, ou seja, os parâmetros "-ti".
se você já tem o container configurado, com sua aplicação e todas as dependências sanadas, não tem a necessidade de usar o modo interativo -- nesse caso utilizamos o parâmetro "-d", ou seja, o container daemonizado.

> Run: quando roda o run, se a imagem não existia em nosso host, ele começa a baixar do Docker Hub

* RUN x CREATE: 
> `docker container create -ti ubuntu`

O RUN cria o container e já inicializa ele, o CREATE apenas cria o container (sendo necessário dar o "start").

* EXECUTAR O CONTAINER E NÃO ABRIR O TERMINAL INTERATIVO
>`docker container run -d nginx`

* SAIR DO TERMINAL INTERATIVO SEM MATAR O CONTAINER
>`ctrl + p + q`


* PARA CONECTAR/ENTRAR NO TERMINAL DO CONTAINER
> `docker container attach [id do container ou nome]`







