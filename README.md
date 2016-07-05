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

Getting the Ca Certs file:

You can use Docker and Alpine to get this!

```
docker run -v $PWD:/certs alpine /bin/sh -c 'apk --update upgrade && apk add curl ca-certificates && update-ca-certificates && cp /etc/ssl/certs/ca-certificates.crt /certs'
```

Examine the size of the resultant image by:

```
docker history golang-test-service
```

It's pretty small!  My output gave me

```
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
4035db88817b        3 hours ago         /bin/sh -c #(nop)  CMD ["/main"]                0 B
9188fd0cc20d        3 hours ago         /bin/sh -c #(nop) %s %s in %s  ADD file:4c976   7.636 MB
edf5ead17421        3 hours ago         /bin/sh -c #(nop) %s %s in %s  ADD file:c6245   274.3 kB
```
