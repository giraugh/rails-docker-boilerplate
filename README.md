# rails-docker-boilerplate
Minaimal rails docker boiler palte

## To Boostrap

Build the container

```bash
docker-compose build
```

Create the rails project

```bash
docker-compose run --rm web rails new . --force --database=postgresql
```

Update the `config/database.yml` config file with the following:

```yml
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: admin
  password: password
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
development:
  <<: *default
  database: myapp_development
```

Start the database:

```bash
docker-compose up db
```

Then, in a seperate terminal process,

```bash
docker-compose run --rm web rails db:create
```

Now close the db terminal process and then start both again:

```bash
docker-compose up

```

You can now visit `localhost:3000` to see your project!
