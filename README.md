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
    - hostname: `computer-1`
    - user: `client1`

1. client2
    - hostname: `computer-2`
    - user: `client2`
