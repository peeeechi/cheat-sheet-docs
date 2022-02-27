# git 関連

## gitのサブコマンド
|コマンド|実行内容|
|:--|:--|
|`clone`|リポジトリのクローンを作成する|
|`init`|リポジトリを新規作成する、または既存のリポジトリを初期化する|
|`remote`|リモートリポジトリを関連付けする|
|`fetch`|リモートリポジトリの内容を取得する|
|`pull`|リモートリポジトリの内容を取得し、現在のブランチに取り込む（「fetch」と「merge」を行う）|
|`push`|ローカルリポジトリの変更内容をリモートリポジトリに送信する|
|`add`|ファイルをインデックスに追加する（コミットの対象にする）|
|`rm`|ファイルをインデックスから削除する|
|`mv`|ファイルやディレクトリの名前を変更する|
|`reset`|ファイルをインデックスから削除し、特定のコミットの状態まで戻す|
|`status`|ワークツリーにあるファイルの状態を表示する|
|`show`|ファイルの内容やコミットの差分などを表示する|
|`diff`|コミット同士やコミットとワークツリーの内容を比較する|
|`commit`|インデックスに追加した変更をリポジトリに記録する|
|`tag`|コミットにタグを付ける、削除する、一覧表示する|
|`log`|コミット時のログを表示する|
|`grep`|リポジトリで管理されているファイルをパターン検索する|
|`branch`|ブランチを作成、削除、一覧表示する|
|`checkout`|ワークツリーを異なるブランチに切り替える|
|`merge`|他のブランチやコミットの内容を現在のブランチに取り込む|
|`rebase`|コミットを再適用する（ブランチの分岐点を変更したり、コミットの順番を入れ替えたりできる）|
|`config`|現在の設定を取得、変更する|


## git remote

### 主なサブコマンド

|サブコマンド|対象|意味|
|:--|:--|:--|
|`add`|名前 URL|現在のローカルリポジトリにリモートのリポジトリを追加する（※2）|
|`remove`|名前|現在のリポジトリからリモートのリポジトリを削除する|
|`rm`|名前|removeと同じ（本文を参照）|
|`rename`|名前 新しい名前|リモートの名前を変更する|
|`set-url`|名前 URL|リモートのURLを変更する（「--add」で追加、「--delete」で削除）|
|`get-url`|名前|リモートのURLを表示する|
|`set-head`|名前|リモートのデフォルトブランチを設定する|
|`set-branches`|名前 ブランチ|リモートで追跡するブランチを変更する（ブランチは複数指定可能、変更ではなく追加したい場合は「--add ブランチ名」とする）|
|`prune`|名前|リモートの追跡ブランチを削除する（「-n」または「--dry-run」オプションを付けると実行せずに、実行する内容だけを表示する）|
|`show`|名前|リモートの情報を詳しく表示する|

## git remote addの主なオプション
|オプション|意味|
|:--|:--|
|`-t ブランチ`|変更を取得するブランチを指定する（デフォルトはmaster、複数を指定可能）|
|`-m ブランチ`|HEAD（先頭）に設定するブランチを指定する|
|`--tags`|全てのタグを取得する（※3）|
|`--no-tags`|タグを取得しない（※3）|
|`--mirror=fetch`|リモートリポジトリからの取得（fetchやpull）時に、全てのブランチやタグを取得する|
|`--mirror=push`|リモートリポジトリへの送信（push）時に、全てのブランチやタグを送信する|
|`-f`|リポジトリを追加した後、リモートリポジトリの変更内容を取得（fetch）する|