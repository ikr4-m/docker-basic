FROM docker.io/library/golang:1.23-alpine AS builder
WORKDIR /app
RUN apk add --no-cache gcc musl-dev
COPY . .
RUN set -ex; \
    go get -C .; \
    go build -C . -ldflags="-linkmode external -extldflags -static -w -s"

FROM docker.io/library/alpine:latest
WORKDIR /app
COPY --from=builder /app/simple-webapp /app
EXPOSE 8080
CMD ["/app/simple-webapp"]

