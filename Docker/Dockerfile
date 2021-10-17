FROM golang:1.15

#$GOPATHに/go/srcを追加．この後srcの下にアプリケーションフォルダを作成する為
ENV GOPATH $GOPATH:/go/src

ENV ROOT=/go/src/app
ENV CGO_ENABLED 0
WORKDIR ${ROOT}

# 必要なパッケージなどをインストールする
RUN apt-get update && \
    apt-get upgrade -y

# go modulesを利用してライブラリを導入する
# COPY go.mod go.sum ./
# RUN go mod download

# install revel and revel-cli
RUN go get github.com/revel/revel && \
    go get github.com/revel/cmd/revel && \
    go get github.com/jinzhu/gorm && \
    go get github.com/go-sql-driver/mysql && \
    go get github.com/revel/modules/static && \
    go get github.com/garyburd/redigo/redis && \
    go get github.com/patrickmn/go-cache && \
    go get github.com/bradfitz/gomemcache/memcache

COPY ./Docker/scripts/start.sh /go/src/

#revelはポート9000で実行されるのでポート9000の開放
EXPOSE 9000

# ginは8080ポートで実行される
# EXPOSE 8080

# CMD ["go", "run", "main.go"]