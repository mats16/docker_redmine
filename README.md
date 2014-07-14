## Redmine on Docker

![docker_redmine](https://docs.google.com/drawings/d/1_6B6OK2_lRWvLDFalXHAcjiSmQTVZ5DmsUGANLmRZJg/pub?w=960&h=720)

### Usage

```bash
$ docker run -d --name <DB_CONTAINER> mattuso/redmine_mysql
$ docker run -d --name <APP_CONTAINER> --link <DB_CONTAINER>:db mattuso/redmine_unicorn
$ docker run -d --name <WEB_CONTAINER> --link <APP_CONTAINER>:app mattuso/redmine_nginx
```