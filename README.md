# Demo Phoenix application

This repo is a Phoenix app demonstrating how to make it run at a configurable 
subdirectory path. It is to go with 
[this article](https://nathansplace.uk/articles/deploying-a-phoenix-app-at-a-configurable-path)
which I wrote.

There is a main branch demonstrating the right answer, and another called `wrong` showing the failed attempt discussed in my article.

## Make it run

You will need a recent version of docker installed. At the time of writing this I was on Docker version `26.1.3, build b72abbb`.

Then, cd into project directory, and run:

```sh
  docker compose up --build
```

This starts:

- Nginx
- Postgres
- and this Phoenix application

See `docker-compose.yml` for details.

Then visit `http://localhost:8080/some_sub_directory` to see it run.