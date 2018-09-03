FROM golang

EXPOSE 3000

RUN apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y install sqlite3 libpam0g-dev postgresql postgresql-client sudo nginx

RUN adduser --disabled-login --gecos 'Gogs' git && \
	sudo mkdir -p /var/log/gogs && \
	sudo chown git:git /var/log/gogs && \
	sudo -H -u git mkdir -p $GOPATH/src/github.com/gogs/gogs/custom/conf && \
	sudo -H -u git mkdir -p ~/gogs-repositories

RUN service postgresql start && \
	sudo -u postgres psql -d template1 -c "CREATE USER git CREATEDB;" && \
	sudo -u postgres psql -d template1 -c "CREATE DATABASE gogs_production OWNER git;" && \
	sudo -u postgres psql -d template1 -c "ALTER USER git WITH ENCRYPTED PASSWORD 'coolpwd';"

RUN go get -v -u -tags "pam cert" github.com/gogs/gogs && \
	cd $GOPATH/src/github.com/gogs/gogs && \
	go build -v

CMD service postgresql start && sudo -H -u git $GOPATH/src/github.com/gogs/gogs/gogs web
