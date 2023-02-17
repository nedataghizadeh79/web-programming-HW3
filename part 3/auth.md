## Dockerfile

this file is placed at the root directory
also, you could either change the golang version from here or the go.mod file to match each other.
<div>

```Dockerfile
FROM golang:1.17-alpine
WORKDIR /usr/src/goapp
COPY go.mod ./
COPY go.sum ./
COPY *.go ./
Copy models/*.go ./models/
COPY utils/*.go ./utils/
COPY certs/* ./certs/
RUN go mod tidy -compat=1.17
RUN go build -o /docker-go-sha
EXPOSE 9000
CMD [ "/docker-go-sha" ]
```

</div>

## command

sudo docker build . -t shahab/auth
sudo docker run -p 9000:9000 shahab/auth