# save!メソッド
``save!(*arg)
``

`save!`メソッドは、引数を取ってオプションを指定できる
- `save!(validate: false)`とすれば、validationはスキップされる
- `save!(touch: false)`とすると、updated_by, updated_atの値がdefalutでは自動で現在の日時が入るが、それをスキップできる


```ruby
item = Item.new(name: 'suger')
item.save!(validate: false)
```
