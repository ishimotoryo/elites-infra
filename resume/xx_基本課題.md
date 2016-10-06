## xx_基本課題（編集中！）

1）`Customers`コントローラーに`before_action`を定義し、show/edit/destroy/updateの共通処理をまとめてください<br>
<br>

2）`Customer`モデルの`body`について、入力可能文字数が最大200文字になるようにバリデーションを追加してください<br>
エラーになった場合、`customers/show`のビューでエラーを表示するように修正してください<br>
<br>
:bulb:ヒント<br>
`CommentsController`の`create`アクションでバリデーションが実行される<br>
エラーだった場合、`CommentsController`から`Customers`の`show`のビューにリダイレクトする<br>
他のコントローラーのビューを表示する場合、`template`オプションを使用し、`render template: "customers/show"`とする<br>
リダイレクトさせた時に`customers/show`のビューで使用する`@customer`と`@comments`の変数にデータを入れる必要がある<br>

イメージ
![](images/crm-comment-error.png)
