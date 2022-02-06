FROM ruby:3.1.0-alpine3.15

# ENV LANG=C.UTF-8 \
#   TZ=Asia/Tokyo

# WORKDIR /app

# RUN apt-get update -qq && apt-get install -y nodejs default-mysql-client
# COPY Gemfile /app/Gemfile
# COPY Gemfile.lock /app/Gemfile.lock
# RUN bundle install

# CMD ["rails", "server", "-b", "0.0.0.0"]

RUN apk add --update-cache --no-cache tzdata libxml2-dev curl-dev \
  make gcc libc-dev g++ linux-headers \
  mysql-dev mysql-client nodejs git yarn && \
  rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock

RUN gem install bundle && bundle install

RUN rm -rf /usr/local/bundle/cache/* /workdir/vendor/bundle/cache/*

COPY . /app