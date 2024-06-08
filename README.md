# Notes on using Docker

## Starting the Docker Daemon

### macOS

1. Install the Docker desktop app (apparently necessary to run the Docker daemon)
```
brew install --cask docker
```
The desktop app also provides the `docker` command-line utility, located at `/usr/local/bin/docker`.

2. Run the Docker desktop app

### Linux

TBD

### Windows

TBD

## Building the Image

Run the following command from instide the `ubuntu-mpc` folder:
```
docker build --no-cache -t ubuntu-mpc:latest .
```

## Running a Container and Getting a Command Prompt

```
docker run -it -h my_project --entrypoint /bin/bash ubuntu-mpc:latest
```

Here, `my_project` becomes the "host" name while the container is running (useful to remember what prompt we are looking at).

## Mounting a Local Folder or Docker Volume

If `/local/folder` already exists on the user's disk,
```
docker run -it -h my_project --entrypoint /bin/bash -v local/folder:/var/lib/external-drive ubuntu-mpc:latest
```

While the container is running, anything written to `/var/lib/external-drive` will persist and be stored under `/local/folder`.

A similar effect can be achieved with *Docker volumes*, which are Docker-specific folders that can be used to hold data related to containers (as opposed to a local folder, that would typically hold data related to the user's host system):

```
docker volume create mpc-092023-00064  # TE data related to this submission
docker run -it -h my_project --entrypoint /bin/bash -v mpc-092023-00064:/var/lib/external-drive ubuntu-mpc:latest
```

When the user exits the container, then runs it again, anything written to `/var/lib/external-drive` is still there, but is not part of the container itself.
