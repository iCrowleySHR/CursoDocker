# Curso de Docker

Veja os conteúdos abaixo

---

## Projeto 1

Nele criamos um **Hello World** em Node.js e configuramos o Dockerfile (arquivo comentado), criamos uma imagem e rodamos o container.

### Como criar uma imagem

Após você configurar o **Dockerfile** da sua aplicação, você deve criar a imagem para depois roda-lá 

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
