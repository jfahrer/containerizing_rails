# Assignment 7 - Glueing things together
Before we get started, make sure to stop all running containers. `docker container ls` and `docker container stop` are your friends here. Once you are done, let's remove all containers that we created in previous assignments. Either with `docker container prune` (**!!Attention!!** this will delete all stopped containers on your system) or manually with `docker container rm`.

## Preparing the Compose file
Now that we have a clean environment, let's put the `docker-compose.yml` in place:
```
cp _examples/docker-compose.yml .
```

Take some time to get familiar with the content of the file.

## Starting the services
Open the file and make the changes in the appropriate places. This should just be the name of the image that will be used. Once you are done, go ahead and start the environment with:
```
docker-compose up -d
```

The `-d` flag will start all services in the background. This allows us to keep working in our current shell.

We can make sure that all services are running with
```
docker-compose ps
```
You should see two containers. The `State` column should say `Up`.

In order to see what our containers tell us on `STDOUT` we can use the following command:
```
docker-compose logs
```

We can also append some additional flags to the `docker-compose logs` command. Use the `--help` option to find out more.

## Getting the app up and running
Try browsing http://localhost:3000 - you will see that the database has not been migrated. That makes sense, we just created a whole new set of containers and volumes. Docker Compose automatically prefixes all resources with the project name (the name of the current directory per default). So let's run the migrations. Just as with the Docker CLI, we can run arbitrary commands in the context of a service:
```
docker-compose run --rm app rake db:create db:migrate
```

Now the web application should work as expected. The `--rm` in the command deletes the container right after it terminates. This is useful because we don't have to clean up after ourselves.

Let's try that again, but this time we will run the test suite:
```
docker-compose run --rm app rspec
```

```
docker-compose run --rm app rails c
```
Note that we don't have to specify the `-it` flags with `docker-compose run`. 

### Bonus
What will happen if you just run the following command:
```
docker-compose run --rm app
```

Any idea why?

[Back to the overview](../README.md#assignments)
