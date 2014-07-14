## Nginx Container

The dockerfile builds nginx image

![docker_redmine_nginx](https://docs.google.com/drawings/d/1rcVPHYIk-Ntphe7NM07FUNOR65qcNOqOvoMJ_rh1qD4/pub?w=960&h=720)

- `CentOS` 6.5
- `nginx` 

### Usage

```bash
$ docker run -d --name <WEB_CONTAINER> --link <APP_CONTAINER>:app -p 80:80 mattuso/redmine_nginx
```