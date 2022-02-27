# Shell

## 配列

### 宣言

```bash
str_arr=("str1" "str2")
int_arr=(1 2 3)
```

### 追加

```bash
str_arr=("${str_arr[@]}" "addtional string")
```

### 連結

#### `' '`で連結(標準)
```bash
concat_str="${str_arr[*]}"
```

#### 連結子を変更して連結
```bash
# ',' で連結
IFS=","
concat_str="${str_arr[*]}"
```

## if

### オプション

|オプション|使用例|オプションの意味|
|:--|:--|:--|
|`-z`|`-z string`|string の文字列長が 0 ならば真となる。|
|`-n`|`-n string`|string の文字列長が 0 より大ならば真となる。|
|`-d`|`-d file`|file がディレクトリならば真となる。(存在確認も兼ねる)|
|`-f`|`-f file`|file が普通のファイルならば真となる。|
|`-s`|`-s file`|file が 0 より大きいサイズならば真となる。|
|`-e`|`-e file`|file が存在するならば真となる。|
|`-r`|`-r file`|file が読み取り可能ならば真となる。|
|`-w`|`-w file`|file が書き込み可能ならば真となる。|
|`-x`|`-x file`|file が実行可能ならば真となる。|

### 複数条件

#### AND 条件
```bash
if test 条件式1 -a 条件式2; then
  ...
fi
```

#### OR 条件
```bash
if test 条件式1 -o 条件式2; then
  ...
fi
```

#### AND 条件と OR 条件
```bash
if test 条件式1 -a 条件式2 -o 条件式3; then
  ...
fi
```

## 多段SSH,SFTP

```bash
sftp -o "ProxyCommand ssh {踏み台ユーザー}@{踏み台IP} -W %h:%p" {接続先ユーザー}@{接続先IP}
```