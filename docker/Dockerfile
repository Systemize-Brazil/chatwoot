# Base image for dependencies
FROM ruby:3.0.5-slim-buster

# Set working directory
WORKDIR /app

# Install dependencies
RUN apt-get update && apt-get install -y \
  build-essential \
  curl \
  git \
  libpq-dev \
  postgresql-client \
  nodejs \
  yarn \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Install specific version of Bundler
RUN gem install bundler:2.3.26

# Clone Chatwoot repository
RUN git clone https://github.com/chatwoot/chatwoot.git ./

# Checkout specific version (v3.13.0)
RUN git checkout v3.13.0

# Install Ruby dependencies
RUN bundle config set without 'development test' && bundle install

# Install Node.js dependencies and build assets
RUN yarn install && yarn build

# Expose port 3000
EXPOSE 3000

# Start the application using foreman
CMD ["bundle", "exec", "foreman", "start"]
