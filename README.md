# Curso de Docker

Veja os conteúdos abaixo.

---

## Imagens no Docker

São com base no Dockerfile que você cria a imagem, no momento que você executa, vira um container

### Para adicionar TAG na criação da sua imagem

```bash
docker build -t meu-usuario/minha-build:1.0.0 .
```

### Para conferir as imagens com suas tags

```bash
docker images
```

### Para remover alguma imagem 

```bash
docker image rm {nome ou image id}
```

### Para zipar e salvar imagem para passar pra outro computador

```bash
docker image save -o nome.tar {nome ou image id}
```

Para carregar imagem em outro máquina

```bash
docker image load -i nome.tar 
```

### Instalar imagem do DockerHub

Para instalar imagens já criadas e rodar, você pode utilizar o comando abaixo.
Nesse exemplo ele instala a imagem do ubuntu e roda automaticamente no seu terminal
Confira todas as imagens no <a href="https://hub.docker.com/">https://hub.docker.com/</a>

`Modo interativo: Quando fechar o terminal, ele desistala o serviço`

```bash
docker run -it ubuntu # Com o -it, roda de modo interativo.
```

---

## Containers no Docker

Para verificar todos os containers rodando na sua máquina.

```bash
docker ps
```

Para verificar todos os containers criados na sua máquina.

```bash
docker ps -a
```

### Parar e iniciar containers
Use o comando abaixo para ver todos os containers ativos:
```bash
docker ps
```

Exemplo de saída:
```bash
Copiar código
CONTAINER ID   IMAGE           COMMAND         STATUS         NAMES
abc123def456   nginx:latest    "nginx -g ..."  Up 5 minutes   meu-nginx
```

Pode usar:

```bash
docker stop meu-nginx
```

ou

```bash
docker stop abc123def456
```

### Para rodar containers já criados

Para rodar container já criados você deve usar o:

```bash
docker ps -a
```

Exemplo de saída:
```bash
Copiar código
CONTAINER ID   IMAGE           COMMAND         STATUS                        NAMES
abc123def456   nginx:latest    "nginx -g ..."  Exited (255) 29 minutes ago   meu-nginx
```

E para iniciar:

```bash
docker start meu-nginx
```

### Para nomear containers

Na hora de criar o container, basta:

```bash
docker run -d --name meu-container imagemUsada
```


### Para visualizar os logs
Com a informação do `docker ps -a`, você pode usar o:

```bash
docker logs -f id ou nomeDoContainer
```

Exemplo de saída:
```bash
Using sqlite database at /etc/todos/todo.db
Listening on port 3000
```

### Para rodar comando de terminal dentro do container

```bash
Copiar código
CONTAINER ID   IMAGE           COMMAND         STATUS                        NAMES
abc123def456   nginx:latest    "nginx -g ..."  Exited (255) 29 minutes ago   meu-nginx
```

Para isso você deve:
```bash
docker exec meu-nginx ls -a # Comandos linux como pwd e etc...
```

ou para abrir o shell do seu container:

```bash
docker exec -it nomeDoContainer sh
```


### Deletar um container

Basta usar o comando abaixo:

```bash
docker rm meu-nginx # nome do container 
```

Para forçar a remoção, é necessário usar o parâmetro -f

```bash
docker rm -f meu-nginx # nome do container 
```


---

## Projeto 1

Nele criamos um **Hello World** em Node.js e configuramos o Dockerfile (arquivo comentado), criamos uma imagem e rodamos o container.

### Como criar uma imagem

Após você configurar o **Dockerfile** da sua aplicação, você deve criar a imagem para depois roda-lá.
Isso fará com que crie o ambiente pra rodar a sua aplicação

```bash
docker build -t nomedabuild .
```


### Rodar o projeto e o container

Após criar a imagem, podemos rodar ela com:

```bash
docker run nomedabuild
```

Com isso rodamos um projeto Node sem a necessidade de instalar manualmente, apenas com os requisitos da imagem.

---

## Projeto 2

Iremos criar o Dockerfile com toda a configuração para rodar a aplicação Node


Quando criamos o container, rodamos uma mini máquina virtual que roda aquele ambiente que criamos.
Podemos acessar o shell com o comando abaixo quando rodarmos a imagem

`Modo interativo: Quando fechar o terminal, ele desistala o serviço`

```bash
docker run -it nomedabuild sh # Com o -it, roda de modo interativo.
```


Para rodar o Dockerfile

```bash
docker build -t projeto2 .
```

Para rodar: *ATENÇÃO, DEPOIS DE CRIADO, VOCÊ PODE USAR O `DOCKER START` PARA RODAR CONTAINER JÁ CRIADOS AO INVÉS DE CRIAR NOVOS*
```bash
docker run -p 3000:3000  projeto2  #-p para liberar a porta 3000
```

Caso queira rodar em backgroud use (Deixa o terminal livre para uso):
```bash
docker run -dp 3000:3000  projeto2  #-d rodar em backgroud
```

## Projeto 3

Projeto onde temos frontend e backend, e será utilizado o `Docker-Composer` para manipular diversas imagens em um único arquivo.
