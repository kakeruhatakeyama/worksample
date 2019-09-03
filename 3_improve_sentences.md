# 「selfについて」説明文が難しかったです。
## selfはインスタンスオブジェクト自身を指しています。クラスの中でインスタンスオブジェクトを呼び出す際やそのインスタンスオブジェクトを呼び出す際は、selfを使用します。

rubyの「self」はオブジェクトそのものを指しています。  
※オブジェクトとは変数とメソッドなどをまとめ、名前を付けた物です。
例えば以下のコードを見てみましょう。

class Menu
 def show_name
  puts "#{self.name}"
 end
end
menu1 = Menu.new
menu1.name = "太郎"
menu1.show_name
