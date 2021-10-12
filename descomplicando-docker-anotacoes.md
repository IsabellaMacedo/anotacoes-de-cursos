# DESCOMPLICANDO O DOCKER (LinuxTips)


### Documentação:

Docker: https://docs.docker.com/get-started/ <br />
Livro Descomplicando o Docker: https://livro.descomplicandodocker.com.br/


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

* CONTAINER ID -- Identificação única do container.
* IMAGE -- A imagem que foi utilizada para a execução do container.
* COMMAND -- O comando em execução.
* CREATED -- Quando ele foi criado.
* STATUS -- O seu status atual.
* PORTS -- A porta do container e do host que esse container utiliza.
* NAMES -- O nome do container.

