# Dockerを使用したサーバ構築

## server1の解説

### イメージ及びコンテナの起動

sv1ディレクトリに移動

```shell
cd sv1
```

以前のキャシュを使用せずビルドする

```shell
docker-compose build --no-cache
```

コンテナを起動する

```shell
docker-compose up -d
```

起動しない場合、コンテナのネットワークを参照し、デフォルト状態以外のネットワークは消す(以下はデフォルト状態)

```shell
docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
3d3e8d5a1de4   bridge    bridge    local
c22841000a5b   host      host      local
7859a2e75126   none      null      local
```

```shell
docker network rm `NAME`
```

コンテナが正常に起動すれば以下のようになる

```shell
 [+] Running 2/2
 - Container apache Started      6.0s 
 - Container bind Started        5.7s    
```

### bindの設定

コンテナに/bin/bashで起動

```shell
docker exec -it bind /bin/bash
```

ファイアウォールのサービス設定

```shell
firewall-cmd --add-service dns
firewall-cmd --add-service dns --permanent
firewall-cmd --reload
```

namedとfirewallの再起動

```shell
systemctl restart named
systemctl restart firewalld
```

### apacheの設定

コンテナに/bin/bashで起動

```shell
docker exec -it apache /bin/bash
```

コンテナのDNSサーバ指定

```shell
vi /etc/resolv.conf
```

- nameservaer 127.0.0.11を172.18.0.2に変更

ファイアウォールのサービス設定

```shell
firewall-cmd --add-service http
firewall-cmd --add-service http --permanent
firewall-cmd --add-service https
firewall-cmd --add-service https --permanent
firewall-cmd --reload
```

apacheとfirewalldの再起動

```shell
systemctl restart httpd
systemctl restart firewalld
```
