docker-rails
========

> This README would normally document whatever steps are necessary to get the
application up and running.

## Getting Started

Have **Docker** and **docker-compose** [installed](https://docs.docker.com/compose/install/).

Fork this project, and do a `git clone` from your fork.

```
cd docker-rails
docker-compose up
```

If all’s well, you should see some PostgreSQL output, and then—after a few seconds—the familiar refrain:

```
myapp_web_1 | [2014-01-17 17:16:29] INFO  WEBrick 1.3.1
myapp_web_1 | [2014-01-17 17:16:29] INFO  ruby 2.2.0 (2014-12-25) [x86_64-linux-gnu]
myapp_web_1 | [2014-01-17 17:16:29] INFO  WEBrick::HTTPServer#start: pid=1 port=3000
```

Finally, you need to create the database. Ctrl-C and run:

```
docker-compose run web rake db:create
```

Note that for rails and rake commands, you will need to prefix it with `docker-compose run web ...`

Run `docker-compose up` again and the Rails application should be running at `<container-ip>:3000`, where `<container-ip >` can obtained from `docker inspect <container id>` or `boot2docker ip`.

A normal development workflow is:

- You run `docker-compose up`
- You preview the running rails application
- You make changes to the rails code
- Restart the rails app by re-running `docker-compose up`
- Your newly changed application runs