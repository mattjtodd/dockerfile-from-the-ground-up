# Dockerfile from the ground up

## From Scratch!

You can statically compile Go using the golang Dockerfile.

```
docker run --rm -v "$PWD/main":/usr/src/main -w /usr/src/main -e GOOS=linux -e CGO_ENABLED=0 golang:alpine go build -v
```

And build the resultant docker file using:

```
docker build -t golang-test-service .
```

And run it using:

```
docker run golang-test-service
```
