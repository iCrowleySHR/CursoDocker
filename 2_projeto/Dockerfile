# Adiciona um Alpine Linux preparado com Node.js 12
FROM node:12-alpine

# Define o diretório /app de trabalho dentro do contêiner
WORKDIR /app

# Copia todos os arquivos do projeto para o diretório de trabalho
COPY . .

# Não se pode usar outro FROM para instalar, pois iniciaria outro Alpine do zero com Python ao invés de adicionar ao atual.
# Instala no Alpine o Python 3, g++ e make. Outras dependências do projeto.
# Roda o comando no terminal
RUN apk add --no-cache python3 g++ make
RUN yarn install --production

# Roda o comando node pelo terminal
CMD ["node", "src/index.js"]

# Libera a porta 3000 para acesso externo
EXPOSE 3000
