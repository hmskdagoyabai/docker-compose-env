# docker-compose-env
docker-composeでnginxコンテナとwebアプリコンテナを起動させる構成の外枠

## 構造

だいたいこんな感じ。

```
.
├── README.md
├── dockerfiles
│   ├── docker-compose.yaml
│   ├── app1
│   │   └── Dockerfile
│   ├── app2
│   │   └── Dockerfile
│   ├── nginx
│   │   ├── Dockerfile
│   │   └── nginx.conf
│   :
│
├── shell
│   ├── end.sh
│   ├── endsuper.sh
│   └── start.sh
│
├── app1
│   ├── app.py
│   ├── config
│   │   └── guniconf.py
│   ├── requirements.txt
│   :
│
└── app2
    ├── app.py
    ├── config
    │   └── guniconf.py
    ├── requirements.txt
    :

```

## rootingを追加するときやること
- プロジェクト直下にアプリフォルダをクローン(ex.`app1`)
- `アプリフォルダ/config/guniconf.conf`にgunicorn設定を記載
- `dockerfiles`フォルダにアプリ名フォルダを作成し`Dockerfile`を用意
- `docker-compose.yaml`にアプリコンテナの設定を追加
- `/dockerfiles/nginx/nginx.conf`にルーティング設定を追加

ポート設定・エイリアス設定に注意！

## スクリプト説明
- `start.sh`
起動
```
$ docker-compose -f dockerfiles/docker-compose.yaml up &
```
- `end.sh`
終了
```
$ docker-compose -f dockerfiles/docker-compose.yaml down
```
- `endsuper.sh`
イメージを削除して終了
```
$ docker-compose -f dockerfiles/docker-compose.yaml down  --rmi all --volumes
```
