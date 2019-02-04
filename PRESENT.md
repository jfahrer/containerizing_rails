# Preprare WS
```
docker container ls -aq | xargs docker container rm -f
docker image prune -a
docker volume ls -q | xargs docker volume rm
```
