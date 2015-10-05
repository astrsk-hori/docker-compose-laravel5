# docker-compose-laravel5
docker-composeでlaravel5環境を構築

## docker-compose install

参考：http://qiita.com/spesnova/items/6e8919b34e763f27c34e
上記のサイト見れば問題なくできるが一応作業手順も記述しておく。

vagrantで起動しているCoreOSにインストールする。

https://github.com/docker/compose/releases

上記で最新のインストール方法をチェックしてcoreos用に少し改良。
→参考サイトにも書いてあるが、coreosは`/usr`配下がreadOnlyの為、配置場所を変更してる。

```
sudo mkdir -p /opt/bin

curl -L https://github.com/docker/compose/releases/download/1.4.2/docker-compose-`uname -s`-`uname -m` > ~/docker-compose

sudo mv ~/docker-compose /opt/bin/
sudo chown root:root /opt/bin/docker-compose
sudo chmod +x /opt/bin/docker-compose
```

正常にインストールされたか確認

```
core@core-01 ~ $ docker-compose --version
docker-compose version: 1.4.2
```

## コンテナ作成

```
docker-compose build
```

## コンテナ起動

```
docker-compose up -d
```

## webサーバに接続

```
docker exec -it la5-php
```

### laravel

既にcomposerも入っているので好きな場所でlaravelのプロジェクトを作成

```
composer create-project laravel/laravel /var/www/html/test --prefer-dist 
```
