FROM golang:1.21 as build

WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 go build

FROM gcr.io/distroless/static-debian12:latest-amd64 as final

COPY --from=build /app/catgpt .
EXPOSE 8080
EXPOSE 9090
CMD ["/catgpt"]