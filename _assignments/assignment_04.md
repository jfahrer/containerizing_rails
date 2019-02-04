# Assignment 4 - Talking to a service
In order to be able to interact with our Rails application over http, we need to publish port `3000`. The following command should do the trick:
```
docker container run -p 3000:3000 your_docker_id/rails_app:v1 rails s
```

As we've seen in prior assignments, we just have to append the command (`rails s`) after the image name. The `-p 3000:3000` flag makes sure that traffic that is received by the Docker Host on port 3000 is forwarded to the container on port 3000.

Open the browser and try to navigate to http://localhost:3000. You should see the Web UI of our demo application.

Back on you command line you should see the output of the Rails server.

Go ahead and try to create a few books via the web interface.

Once you are done, you can terminate Rails and the container by pressing `Ctrl-C`.


## Things to try
* What will happen if you try to start a second container while the first one is still running?
* Stop the current container by pressing `Ctrl-C`. Then start a new container with the same command. Is the data still there?
* Try to figure out how to revive the old container that you stopped earlier. `docker container --help` is your friend. Do you see the data again?


## Troubleshooting
If you receive an error message similar to this one:
```
docker: Error response from daemon: driver failed programming external connectivity on endpoint elastic_robinson (1e9b864796702b7909a3247a04809fe053885367b152d2385ce7ddeab364b6d5): Bind for 0.0.0.0:3000 failed: port is already allocated.
ERRO[0000] error waiting for container: context canceled
```
You are already running something on port 3000. Either stop the service that is bound to port 3000 or change the local port:
```
docker container run -p 3001:3000 your_docker_id/rails_app:v1 rails s
```

[Back to the overview](../README.md#assignments)
