# Docker + Ruby on Rails + Next.js + TypeScript + MySQL

### Railsアプリ作成

```bash
$ docker-compose run api rails new . --f --api --database=mysql
```

api/config/database.ymlを編集

```yaml
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password
  host: db

development:
  <<: *default
  database: webapp_development

test:
  <<: *default
  database: webapp_test

production:
  <<: *default
  database: webapp_production
  username: webapp
  password: <%= ENV["APP_DATABASE_PASSWORD"] %>
```

### Nextアプリ作成（TypeScript）

```bash
$ docker-compose run --rm front yarn create next-app . --typescript
```

### イメージのビルド、コンテナ起動

```bash
$ docker-compose up --build
```

### DB作成

```bash
$ docker-compose run api rails db:create
```
