FROM registry.svc.ci.openshift.org/openshift/release:golang-1.10 AS builder
ENV OPERATOR_PATH=/go/src/github.com/c-e-brumm/false-hive
COPY . ${OPERATOR_PATH}
WORKDIR ${OPERATOR_PATH}
#RUN GOENV=GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build -gcflags="all=-trimpath=${GOPATH}" -asmflags="all=-trimpath=${GOPATH}"  -o build/_output/bin/${OPERATOR_BIN} ./cmd/manager
RUN GOENV=GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build -o build/_output/bin/false-hive ./cmd/manager

FROM registry.access.redhat.com/ubi7/ubi-minimal:latest
ENV OPERATOR_PATH=/go/src/github.com/c-e-brumm/false-hive \
    OPERATOR_BIN=false-hive

WORKDIR /root/
COPY --from=builder ${OPERATOR_PATH}/build/_output/bin/${OPERATOR_BIN} /usr/local/bin/${OPERATOR_BIN}

