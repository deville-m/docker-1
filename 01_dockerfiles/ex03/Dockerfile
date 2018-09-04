FROM golang

EXPOSE 3000

RUN apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y install sqlite3

RUN go get -d -u code.gitea.io/gitea

WORKDIR $GOPATH/src/code.gitea.io/gitea

RUN TAGS="bindata sqlite" make generate build

ENV USER root
ENV DB_TYPE sqlite3

CMD ./gitea web
