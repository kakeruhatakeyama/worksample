>Railsにおける、「単数」と「複数」の使い分けについての説明です。
>
>例えばコントローラー作成時は"blogs"と、モデル作成時は"blog”とそれぞれパラメーター指定させています。それに基づいて様々な変数等が自動的に作成されているようなので、"blogs"と"blog"を使い分けることに意味があるのだと思うのですが、何処にも記載が無いので未だに混乱しています。
>
>rake routes"を行ってみても、Prefixに"blog"　”new_blog"もあれば、"blogs" "confirm_blogs"もあります。何故こうなっているのか全く理解できていません。

命名規則に関しては最初悩みますよね。  
ですが、ちょっと視点を変えればわかりやすい物でもあります！  
まず、Railsは基本的に「言語的慣習」に従っているという点を押さえておきましょう。  

単数と複数の違いですが、単純にそのものが「単数」か「複数」かで分けられています。  
なぜコントローラは複数形なのかについては、  
コントローラーはモデルから作られたインスタンス全てをコントロールするためのものだからです。  
以下に簡単な分類を載せておきますので確認してみてください！  

コントローラー、テーブル…すべてのモデルを1つのコントローラー、テーブルで扱うので、複数形  
モデル…Model.newとすると1レコードだけのモデルができるように、1レコード単位で扱うので単数形  
アソシエーション…has_manyは複数作れるので複数形、belongs_toやhas_oneは1つだけなので単数形  
リクエストパラメーター…通常、一度に1モデルしか編集しないので、単数形  

rake routesコマンドで確認すると以下のようになります。
上記の分類を確認しながら見てみましょう。
```
Prefix    Verb    URI Pattern                Controller#Action
blogs      GET    /blogs(.:format)           blogs#index   → 一覧画面の生成  
blogs      POST   /blogs(.:format)           blogs#create  → 上記一覧にブログ登録 
new_blog   GET    /blogs/new(.:format)       blogs#new     → 新しいブログの登録画面の生成
edit_blog  GET    /blogs/:id/edit(.:format)  blogs#edit    → 特定のブログを編集する画面の生成   
blog       GET    /blogs/:id(.:format)       blogs#show    → 特定のブログの詳細画面の生成
blog       PATCH  /blogs/:id(.:format)       blogs#update  → 特定のブログの更新
blog       PUT    /blogs/:id(.:format)       blogs#update  → 特定のブログの更新
blog       DELETE /blogs/:id(.:format)       blogs#destroy → 特定のブログの削除
```
このように一覧に関係している物は複数形のblogs、特定の記事に関係する物はnew_blogなど単数形となっています。  
まずはその動作や物が複数あるものなのか、単数のものなのかを考えてみればわかりやすいかもしれませんね。
