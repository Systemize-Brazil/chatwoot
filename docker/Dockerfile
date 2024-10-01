# Use a imagem oficial do Ubuntu como base
FROM ubuntu:20.04

# Defina o maintainer (opcional)
LABEL maintainer="contato@systemize.com.br"

# Evite prompts de instalação interativos
# ENV DEBIAN_FRONTEND=noninteractive

# Instale dependências essenciais
RUN apt-get update && \
    apt-get install -y \
    curl \
    sudo \
    wget \
    gnupg2 \
    software-properties-common \
    apt-transport-https \
    ca-certificates \
    lsb-release && \
    apt-get clean

# Baixe o script de instalação do Chatwoot
RUN wget https://get.chatwoot.app/linux/install.sh -O /opt/install.sh

# Conceda permissões de execução ao script
RUN chmod +x /opt/install.sh

# Execute o script de instalação
RUN /opt/install.sh --install <<EOF
no
no
EOF

# Exponha a porta usada pelo Chatwoot
EXPOSE 3000

# Defina o diretório de trabalho
WORKDIR /opt/chatwoot

# Comando para iniciar o Chatwoot (ajuste conforme necessário)
CMD ["chatwoot"]
