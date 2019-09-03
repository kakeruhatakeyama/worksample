# 「selfについて」説明文が難しかったです。
`該当文`
```
selfはインスタンスオブジェクト自身を指しています。  
クラスの中でインスタンスオブジェクトを呼び出す際やそのインスタンスオブジェクトを呼び出す際は、selfを使用します。
```
`修正後`
```
rubyの「self」はオブジェクトそのものを指しています。  
※オブジェクトとは変数とメソッドなどをまとめ、名前を付けた物です。

 class Menu
  def show_name
   puts "#{self.name}"
  end
 end
 menu1 = Menu.new
 menu1.name = "太郎"
 menu1.show_name
 上記のようにselfでインスタンスを指すことができる。self=menu1=Menuになっている。

```
