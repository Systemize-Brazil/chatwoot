# Base image using Ubuntu
FROM ubuntu:20.04

# Definir o diretório de trabalho
WORKDIR /app

# Desabilitar prompts interativos durante a instalação de pacotes
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependências do sistema
RUN apt-get update && apt-get install -y \
  curl \
  git \
  build-essential \
  libpq-dev \
  postgresql-client \
  nodejs \
  yarn \
  imagemagick \
  libxml2-dev \
  libxslt-dev \
  file \
  ruby-full \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Instalar uma versão específica do Bundler
RUN gem install bundler:2.3.26

# Clonar o repositório do Chatwoot
RUN git clone https://github.com/chatwoot/chatwoot.git ./

# Fazer checkout da versão específica do Chatwoot (v3.13.0)
RUN git checkout v3.13.0

# Instalar dependências do Ruby (gems)
RUN bundle config set without 'development test' \
  && bundle install --retry 5 --jobs 4

# Instalar dependências do Node.js e compilar os assets
RUN yarn install && yarn build

# Expor a porta usada pela aplicação
EXPOSE 3000

# Comando de inicialização
CMD ["bundle", "exec", "foreman", "start"]
