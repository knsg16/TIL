# delete_ifメソッド
``array.delete_if {|item| block }
``

delete_ifメソッドは、要素の数だけ繰り返しブロックを実行し、ブロックの戻り値が真になった要素を削除します。レシーバ自身を変更するメソッド。ブロック引数itemには各要素が入る。


```ruby
numbers = 12, 11, 10
numbers.delete_if {|number| number % 2 == 0 }
p numbers
```
`[11]`
