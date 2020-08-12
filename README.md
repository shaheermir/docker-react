Build

```
docker build -t frontend -f Dockerfile.dev .
```

Run

```
docker run \
-it \
--rm \
-v ${PWD}:/app \
-v /app/node_modules \
-p 3000:3000 \
imagename
```

`-it` to run in interactive mode (required for react-scripts ^3.4.0)
`--rm` remove the container and the volumes after container exits
`-v ${PWD}:/app` map the PWD to `/app` folder inside the container
`-v /app/node_modules` Bookmark this folder.
We wanna use the container version of node_modules. (We run npm install as part of build step)
So essentially, we are mapping everything to our PWD, except for the node_modules. We can safely remove
the local node_modules as it is no longer being referenced from inside the container.
`-p` port mapping

We can use docker-compose to shorten our docker run cmd.
