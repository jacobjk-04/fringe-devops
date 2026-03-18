FROM golang:1.21 AS builder

WORKDIR /app
COPY . .
RUN go mod init fringe-backend || true
RUN go mod tidy
RUN go build -o app

FROM debian:bullseye-slim
WORKDIR /
COPY --from=builder /app/app /app

EXPOSE 8000

CMD ["/app"]