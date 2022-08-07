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

```bash
$ ssh -p 2222 user@server.test
```

## Client

### 1

- hostname: `computer-1`
- user: `client1`

### 2

- hostname: `computer-2`
- user: `client2`
