# 02_Linuxの基本

## はじめに
- 最低限のUNIXコマンドを学ぶ
- 全てターミナルでの操作
- 英語ばっかりだけどびっくりしないで冷静に対処

## ターミナルとは
- コマンドと呼ばれる命令文を用いて、Macの操作や設定をおこなうためのアプリ
- ちょっと難しいことをいうと、キーボードでMacと対話するソフト
- Railsに対して、ターミナルで命令を出して開発を進める

## ファイルの種類
 - テキストファイル （Windowsでいう.txtと同じ）
 - バイナリファイル （画像や音声ファイルなど）
 - シンボリックリンク （Windowsでいうショートカットファイル）
 
## ディレクトリとは
- ディレクトリとは「ファイルの保存場所」のこと
- いわゆる"フォルダ"と同じものと考えてOK

![ディレクトリ参考画像](http://webya.in/wp-content/uploads/2012/01/directory.jpg)

## ターミナルを起動する
- 今回はCloud9のコンソールを利用します
- MacOSであればデフォルトのアプリが入っています([アプリケーション] → [ユーティリティ] → [ターミナル])

## コマンドの基本
- 半角英数字を使う(日本語はアウト！)
- コマンドとコマンドの間には**半角スペース**が必要
- コマンドを間違えても`command not found`と出るだけで変なことにはならないので冷静に打ち直す

## ls コマンド
現在のディレクトリ下にあるファイルやフォルダの情報を表示

**l**ist **s**egmentsの略

```bash
$ ls
Applications      Music
Desktop         Pictures
Documents       Public
Downloads       Library
```

## pwd コマンド
現在のディレクトリを確認

**p**resent **w**orking **d**irectoryの略

```bash
$ pwd
/Users/nashirox
```

## cd コマンド
ディレクトリを移動

**c**hange **d**irectoryの略

```bash
$ cd Desktop # デスクトップへ移動
$ pwd
/Users/nashirox/Desktop
$ cd .. # 一つ上のディレクトリへ
$ pwd
/Users/nashirox
```

## mkdir コマンド
ディレクトリを作成

**m**a<strong>k</strong>e **dir**ectoryの略

$ mkdir + [新フォルダ名]

```bash
$ pwd
/Users/nashirox/Desktop
$ mkdir sample_folder
$ ls
sample_folder
```

## cp コマンド
ファイルやディレクトリをコピー

**c**o<strong>p</strong>yの略

```bash
$ cp sample.txt copy.txt # コピー元 コピー先の順番
$ ls
sample.txt  copy.txt
```

### ディレクトリをコピーするには「オプション」が必要
cpコマンドの後に -a オプションをつける。

```bash
$ cp -a sample_folder copy_folder
$ ls
sample_folder copy_folder
```

## vi コマンド
ターミナル内で使えるエディタを起動

**vi**sual display editorの略

$ vi [ファイル名 ...］

- 起動後はコマンドモードだが、`i`を押すと編集モードにはいる。
- 編集モードで`esc`を押すと、コマンドモードに戻る
- コマンドモードで`：wq`を入力すると保存して終了、`:q`だと保存しないで終了
- 存在しないファイル名を指定すると、新しいファイルを作成して編集に入る

多くのコマンドがあるので、より詳しく知りたい方は<a href="http://hp.vector.co.jp/authors/VA016670/unix/vi_reference.html" target="_blank">このサイト</a>などを参照してください。

## touch コマンド
空のファイルを作成できる

```bash
$ touch hoge.txt
$ ls
hoge.txt
```

## mv コマンド
ファイルを別のディレクトリへ移動する

```bash
$ mv hoge.txt hoge/
```

## rm コマンド
ファイルを削除する

```bash
$ rm hoge.txt
```

## その他便利な使い方
- パスを入力中、`tab`を押すと予測してくれる
- `control + a`で最初にカーソルが戻る
- `cd ~`でホームディレクトリに戻れる
- <a href="http://qiita.com/akito/items/d09a2d5b36d4cf7bac6d" target="_blank">ターミナルで使用できるショートカット</a>

## 絶対パスと相対パス
 - 自分がいる場所から別の場所を指定すると、それは**相対パス**となります。
```
../app/

(今自分がいる場所：/home/ubuntu/workspace/config)
```
##### 参考
ドットが2つ（../）は今自分がいるディレクトリの**1階層上**を指します  
ドットが1つ（./）は今自分がいるディレクトリを指します  

 - 自分がいる場所に関係なく、 / (ルートディクトリ)から指定した場所は**絶対パス**となります。下の絶対パスは、上述の相対パスと**同じ場所を指しています**
```
 /home/ubuntu/workspace/app/
```
 
<br />
## 一般的なLinuxのディレクトリ構成
|ディレクトリ名|役割|よく使う|
|:---|:---|:---:|
|/ | ルートディレクトリ（大元） |●|
|/bin | 基本コマンドが入っている |●|
|/boot | 起動に必要なファイルが入っている ||
|/dev | デバイスファイルが入っている ||
|/etc | 設定ファイル |●|
|/home | ユーザー用のディレクトリが入っている |●|
|/lib | 共有ライブラリが入っている ||
|/mnt | 一般的な外部ディスクのマウントポイント ||
|/opt | 追加アプリケーション ||
|/proc | プロセス情報など ||
|/root | rootユーザー用ディレクトリ |●|
|/sbin | システム管理用コマンド ||
|/tmp | 一時ファイル ||
|/usr | 各種プログラムなど ||
|/var | ログやデータベースファイルなどの可変データ |●|

<br />
## 確認問題
1）`ls` コマンドのオプションを調べてリストを縦一列に表示してみましょう。

2）`cd` コマンドで自分のユーザーディレクトリに一発で戻ってみましょう。

3）`mkdir` コマンドにオプションをつけて、今自分がいるディレクトリに `test1/test2/test3` ディレクトリを作ってみましょう。

4)　`cp` コマンドにオプションをつけて、ファイルの所有者・パーミッションを維持したまま `test1.txt` を `test2.txt` にコピーしてください。

## 確認問題の答え
1）　`ls -l`

2)　`cd ~`

3)　`mkdir -p test1/test2/test3`

4)　`cp -p test1.txt test2.txt`
