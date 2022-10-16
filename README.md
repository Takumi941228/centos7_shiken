# Dockerを使用したサーバ構築

## 注意事項

※作成前に、現在のイメージ及びコンテナを全て削除

- ネットワークやポートのかぶりがあるとめんどくさい
- 以前作ったものを全て削除

## 実証

- クアイアントPCの設定
    - IPアドレス：自動取得（192.168.1.139～）
    - 優先DNSサーバ：自動取得（192.168.1.130）
    - プロキシ(192.168.1.130:8080)

- クライアントPCでの実証
    - ブラウザでYahoo!などのインターネットアクセス可能
    - www.j21.jyoho.comでWebページの表示
    - 192.168.1.130でWebページの表示

![構成図2](./image.JPG)
