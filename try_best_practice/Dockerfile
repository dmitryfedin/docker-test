FROM alpine:latest

WORKDIR /app

RUN apt-get update \
    && apt-get upgrade \
    && curl -sL https://deb.nodesource.com/setup_9.x | sudo bash - \
    && apt-get -y install libpq-dev imagemagick gsfonts ruby-full ssh supervisor nodejs \
    && gem install bundler \
    && bundle install --without development test --path vendor/bundle \
    rm -rf /usr/local/bundle/cache/*.gem \
    apt-get clean \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

COPY . /app

CMD [“/app/init.sh”]
