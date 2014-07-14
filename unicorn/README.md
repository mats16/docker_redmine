## Unicorn Container

The dockerfile builds unicorn image (rails & redmine)

![docker_redmine_unicorn](https://docs.google.com/drawings/d/1-bE_LKja5INIx80dY_e2WE3_1d3CyekxfA4oei5YjCA/pub?w=960&amp;h=720)

- `CentOS` 6.5
- `unicorn`
- `ruby` 2.1.0
- `Redmine` 2.5-stable

### Usage

```bash
$ docker run -d --name <APP_CONTAINER> --link <DB_CONTAINER>:db mattuso/redmine_unicorn
```