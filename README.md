# Curso de Docker

Veja os conteúdos abaixo.

---

## Informações

Para verificar todos os containers rodando na sua máquina.

```bash
docker ps
```


Para verificar todos os containers criados na sua máquina.

```bash
docker ps -a
```

Para adicionar TAG na criação da sua imagem

```bash
docker build -t meu-usuario/minha-build:1.0.0 .
```

Para conferir as imagens com suas tags

```bash
docker images
```

Para remover alguma imagem 

```bash
docker image rm {nome ou image id}
```

Para zipar e salvar imagem para passar pra outro computador

```bash
docker image save -o nome.tar {nome ou image id}
```

Para carregar imagem em outro máquina

```bash
docker image load -i nome.tar 
```

# 🛑 Parando Containers no Docker

## 1) Listar containers em execução
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

```bash
docker stop meu-nginx
```

```bash
docker stop abc123def456
```

---



Para instalar imagens já criadas e rodar, você pode utilizar o comando abaixo.
Nesse exemplo ele instala a imagem do ubuntu e roda automaticamente no seu terminal
Confira todas as imagens no <a href="https://hub.docker.com/">https://hub.docker.com/</a>

`Modo interativo: Quando fechar o terminal, ele desistala o serviço`

```bash
docker run -it ubuntu # Com o -it, roda de modo interativo.
```

## Projeto 1

Nele criamos um **Hello World** em Node.js e configuramos o Dockerfile (arquivo comentado), criamos uma imagem e rodamos o container.

### Como criar uma imagem

Após você configurar o **Dockerfile** da sua aplicação, você deve criar a imagem para depois roda-lá.
Isso fará com que crie o ambiente pra rodar a sua aplicação

```bash
docker build -t nomedabuild .
```

---

### Rodar o projeto e o container

Após criar a imagem, podemos rodar ela com:

```bash
docker run nomedabuild
```

Com isso rodamos um projeto Node sem a necessidade de instalar manualmente, apenas com os requisitos da imagem.

## Projeto 2

Iremos criar o Dockerfile com toda a configuração para rodar a aplicação Node

---

Quando criamos o container, rodamos uma mini máquina virtual que roda aquele ambiente que criamos.
Podemos acessar o shell com o comando abaixo quando rodarmos a imagem

`Modo interativo: Quando fechar o terminal, ele desistala o serviço`

```bash
docker run -it nomedabuild sh # Com o -it, roda de modo interativo.
```

---

Para rodar o Dockerfile

```bash
docker build -t projeto2 .
```


```bash
docker run -p 3000:3000  projeto2  #-p para liberar a porta 3000
```

Caso queira rodar em backgroud use:
```bash
docker run -dp 3000:3000  projeto2  #-d rodar em backgroud
```
