FROM golang:1.8
MAINTAINER  singula <singula@singula-point.com>

COPY ./ /go/src/github.com/singula-point/kubernetes-exporter
WORKDIR /go/src/github.com/yunlzheng/kubernates-exporter/
RUN go build

RUN cp kubernates-exporter /bin/kubenates-exporter
ENTRYPOINT [ "/bin/kubenates-exporter" ]

