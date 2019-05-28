# DokcerによるPHP Webサーバ環境

Dockerを活用したPHP利用可能なWebサーバ環境です。

## 実行環境

| ミドルウェア | バージョン |
| :---- | :---- |
| Docker | 18.09.2 |
| docker-composer | 1.23.2 |
| docker-machine | 0.16.1 |

## ディレクトリ構造

```
$ tree
.
├── README.md
├── app                         # Webアプリケーションの保存場所
│   └── index.php
├── assets                      # 資材
│   └── nginx
│       ├── conf.d              ## Nginxのコンフィグ
│       │   └── default.conf
│       ├── nginx.conf          ## Nginxのベースコンフィグ
│       └── ssl                 ## SSL証明書ディレクトリ（※本リポジトリでは自己証明書を利用）
│           ├── server.crt
│           └── server.key
├── containers                  # Dockerコンテナ設定
│   ├── nginx
│   │   └── Dockerfile
│   └── php
│       └── Dockerfile
└── docker-compose.yml
```

## 実行コマンド

* 起動

```
$ docker-compose up &
```

* ページアクセス

```
$ curl https://localhost --insecure
```

* プロセス確認

```
$ docker-compose ps
          Name                        Command              State                    Ports
-----------------------------------------------------------------------------------------------------------
dockernginxlaravel_php_1   docker-php-entrypoint php-fpm   Up      9000/tcp
dockernginxlaravel_web_1   nginx -g daemon off;            Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```

* プロセス停止

```
$ docker-compose down
```
