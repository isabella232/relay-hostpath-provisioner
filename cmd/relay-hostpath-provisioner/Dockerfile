FROM golang:1.14-alpine AS builder
ENV GO111MODULE on
ENV CGO_ENABLED 0
WORKDIR /build
COPY . .
RUN go build -a -ldflags '-extldflags "-static"' -installsuffix cgo -o /relay/hostpath-provisioner ./cmd/relay-hostpath-provisioner

FROM scratch
COPY --from=builder /relay/hostpath-provisioner /relay/hostpath-provisioner
CMD ["/relay/hostpath-provisioner"]
