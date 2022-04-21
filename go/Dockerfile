FROM golang:1.18

# Add Filewatcher
RUN apt update && apt install -y nodejs npm && \
    npm install -g nodemon

RUN go install github.com/go-delve/delve/cmd/dlv@latest

ADD entrypoint /build/entrypoint
RUN chmod +x /build/entrypoint

WORKDIR /app
ADD ./src /app

ENTRYPOINT ["nodemon", "-L", "-e", "go,html", "--exec"]
CMD bash /build/entrypoint && exit 1
