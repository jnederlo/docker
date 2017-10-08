FROM		debian

RUN			apt-get update && \
			apt-get install git -y && \
			apt-get install wget -y

RUN			apt-get update && \
			apt-get install -y --no-install-recommends build-essential ca-certificates \
			git golang-go sqlite libsqlite3-dev openssl openssh-server -y

WORKDIR		/usr/local
RUN			wget https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz
RUN			tar -xvzf go1.8.3.linux-amd64.tar.gz

ENV			GOROOT=/usr/local/go
ENV			GOPATH=/usr/gogs
ENV			PATH=$PATH:$GOROOT/bin:$GOPATH/bin

WORKDIR		$GOPATH/src/github.com/gogits
RUN			git clone --depth=1 -b develop https://github.com/gogits/gogs

WORKDIR		$GOPATH/src/github.com/gogits/gogs
RUN			go build -v -tags 'sqlite'

ENV			USER="root"
EXPOSE		3000
USER		root

CMD			["./gogs", "web"]