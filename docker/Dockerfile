# Base image
FROM chatwoot/chatwoot:latest-ce

# Exemplo de customizações adicionais se necessário
# RUN apt-get update && apt-get install -y <algum-pacote>

# Porta usada pelo Chatwoot
EXPOSE 3000

# Comando de inicialização padrão
CMD ["bundle", "exec", "foreman", "start"]
