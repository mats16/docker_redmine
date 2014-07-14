## MySQL Container

The dockerfile builds mysql image

![docker_redmine_mysql](http://docs.google.com/drawings/d/1F3-zeak2eGoE5jzqtyI5TbZZBEhYldb_pQd4dkX5zVE/pub?w=960&h=720)

- `CentOS` 6.5
- `mysql` 5.5

### Usage

```bash
$ docker run -d --name <DB_CONTAINER> mattuso/redmine_mysql
```