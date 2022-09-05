# Dev Environment
Please use the Visual Studio Code workspace `ws.code-workspace`

Otherwise gopls will get confused over the two golang modules. See [Golang Issue #32394](https://github.com/golang/go/issues/32394)

Requirements:

- Golang 1.17+
- Docker (With Docker Compose)
- Make

# Testing
Testing requires a Docker daemon running

If you make changes to production files (in src), a docker-compose build is necessary.

Notice that the make targets automatically builds for you.

# Manually booting up the docker-compose service

## With Visual Studio Code

#### Start an automatically configured graph/setup of peers
`ctrl+shift+p` &#8594; `Tasks: Run Task` &#8594; `Boot Setup X`

#### To inspect a peer, attach from shell to a docker container *n* with
`ctrl+shift+p` &#8594; `Tasks: Run Task` &#8594; `Inspect container n`

## With a shell

##### Start *n* peer services with
`docker-compose --project-name systemtest up --scale peer=n`

##### To inspect a peer, attach from shell to a docker container *n* with
`docker attach systemtest_peer_n`

# Cleaning up
To stop running containers, run:

`make Cleanup`

As each consequent build will produce a dangling image, your disk can fill up rather quickly. To removing dangling images, run:  

`docker image prune`