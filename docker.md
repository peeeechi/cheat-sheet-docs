# Docker cheat sheet

## docker ps

### fillter

`-f, --filter=[]`  
フィルタリング・フラグ（ -f と --filter ）の形式は key=value の組です。  
複数のフィルタを指定するには、複数のフラグを使います（例： --filter "foo=bar" --filter "bif=baz" ）。  
現在、以下のフィルタをサポートします。  
- id（コンテナの ID）
- label（ label=<key> か label=<key>=<value> ）
- name（コンテナの名前）
- exited（整数値 - コンテナの終了コード。実用的なのは --all）
- status（created|restarting|running|paused|exited|dead）
- ancestor（ <イメージ名>[:<タグ>] 、 <イメージID> 、 <イメージ@digest> ） - 特定のイメージから作られた子コンテナを作成します。
- before（コンテナ ID か名前） - 指定した ID か名前よりも前に作成したコンテナでフィルタ
- since（コンテナ ID か名前） - 指定した ID か名前よりも後に作成したコンテナでフィルタ
- isolation （default|process|hyperv）（Windows デーモンのみ）
- volume（ボリューム名かマウントポイント） - コンテナがマウントしているボリュームでフィルタ
- network（ネットワーク ID か名前）- コンテナが接続しているネットワークでフィルタ

### format

`--format=[]`  
Go テンプレートを使いコンテナの表示を整形

|tag|description|
|:--|:--|
|.ID|コンテナ ID|
|.Image|イメージ ID|
|.Command|クォートされたコマンド|
|.CreatedAt|コンテナが作成された時間|
|.RunningFor|コンテナが起動してからの時間|
|.Ports|公開しているポート|
|.Status|コンテナのステータス|
|.Size|コンテナのディスク容量|
|.Names|コンテナ名|
|.Labels|コンテナに割り当てられている全てのラベル|
|.Label|コンテナに割り当てられた特定のラベル。例： `{{.Label "com.docker.swarm.cpu"}}`|

## Dockerでの便利コマンド

### コンテナIDの一覧を取得する

```bash
docker ps -a -q
```
-q フラグを指定することでコンテナIDのみ取得できる

### 停止しているコンテナを全起動する

```bash
docker start $(docker ps -a -q)
```

### 起動しているコンテナを全停止する

```bash
docker stop $(docker ps -a -q)
```

### 停止しているコンテナを全削除する(rm に -f をつけると起動中のものも含めて全削除)
```bash
docker rm $(docker ps -a -q)
```

docker container prune だと停止中のコンテナの全削除