# Curso de Docker

Veja os conteúdos abaixo.

---

## Informações

Para verificar todos os containers rodando na sua máquina.

```bash
docker ps
```


Para verificar todos os containers criadosna sua máquina.

```bash
docker ps -a
```

---

Para instalar imagens já criadas e rodar, você pode utilizar o:

```bash
docker run -it ubuntu # Com o -it, roda de modo interativo, quando você parar de usar, ele desistala da sua máquina.
```

Nesse exemplo ele instala a imagem do ubuntu e roda automaticamente no seu terminal


## Projeto 1

Nele criamos um **Hello World** em Node.js e configuramos o Dockerfile (arquivo comentado), criamos uma imagem e rodamos o container.

### Como criar uma imagem

Após você configurar o **Dockerfile** da sua aplicação, você deve criar a imagem para depois roda-lÁ.
Isso fará com que crie o ambiente pra rodar a sua aplicação

```bash
docker build -t nomedabuild
```

---

### Rodar o projeto e o container

Após criar a imagem, podemos rodar ela com:

```bash
docker run nomedabuild
```

Com isso rodamos um projeto Node sem a necessidade de instalar manualmente, apenas com os requisitos da imagem.
