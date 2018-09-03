FROM golang

EXPOSE 3000

RUN apt-get -y update && apt-get -y upgrade && apt-get -y install sqlite3 libpam0g-dev sudo

RUN sudo adduser --disabled-login --gecos 'Gogs' git

RUN go get -v -u -tags "sqlite pam cert" github.com/gogs/gogs && \
	cd $GOPATH/src/github.com/gogs/gogs && \
	go build -v

CMD $GOPATH/src/github.com/gogs/gogs/gogs web