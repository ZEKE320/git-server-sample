# 仮想環境

## docker-compose


### 環境を立ち上げる（最初）

```
$ docker-comopse up -d
```

### 環境を落とす（最後）

```
$ docker-comopse down
```

### 環境に入る（server）

```
$ docker-comopse exec server /bin/bash
```

### 環境に入る（client1）

```
$ docker-comopse exec client-1 /bin/bash
```

### 環境に入る（client2）

```
$ docker-comopse exec client-2 /bin/bash
```

## Server

### INFO

- hostname: `server.test`
- ssh-port: `2222`
- user: `user`
- password: `password`

### SSH

#### Config

- sshサーバーがport:`2222`でたっているため、ポートを指定しないといけない
- `config`に記載しておくと楽

```ssh:.ssh/config
Host server.test
Hostname server.test
Port 2222
```

```bash
$ ssh user@server.test
```

## Client

1. client1
    - hostname: `client-1`
    - user: `client1`

1. client2
    - hostname: `client-2`
    - user: `client2`

## Gitの簡易サーバー立て方

1. このRepositoryをcloneしてくる

```
$ git clone https://github.com/kanorix/git-server-sample.git
```

1. 移動して仮想環境を立ち上げる

```
$ cd git-server-sample/
$ docker-compose up -d
```

1. `Server`の環境にはいり、Gitをインストールする

```
$ docker-compose exec server /bin/bash
$ apk --update --no-cache add git
$ exit
```

1. `client-1`の環境にはいり、`project`内で空のReposoitoryを作成

```
$ docker-compose exec client-1 /bin/bash
```

```bash
$ cd project
$ git init
$ git add hello.txt
$ git commit -m "version1"
```

1. 作成したGitReposoitoryをサーバー側にアップロード

```bash
$ cd ..

$ ls
project
$ git clone --bare project project.git
Cloning into bare repository 'project.git'...

$ scp -r project.git user@server.test:/opt/
```

1. remoteの情報を設定

```bash
$ git remote add origin user@server.test:/opt/project.git
```

1. `client-1`の環境から抜ける

```bash
$ exit
```

1. `client-2`の環境にはいり、`clone`してくる

```
$ docker-compose exec client-2 /bin/bash
$ git clone user@server.test:/opt/project.git
$ cd project
```
