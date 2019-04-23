# save!メソッド
## 概要
``save!(*arg)
``

`save!`メソッドは、引数を取ってオプションを指定できる
- `save!(validate: false)`とすれば、validationはスキップされる
- `save!(touch: false)`とすると、updated_by, updated_atの値がdefalutでは自動で現在の日時が入るが、それをスキップできる


```ruby
item = Item.new(name: 'suger')
item.save!(validate: false)
```

## 参考
- [module function FileUtils.#touch (Ruby 2.6.0)](https://docs.ruby-lang.org/ja/latest/method/FileUtils/m/touch.html)
- [Railsでこの時だけ特定のバリデーションを検証したくないときしたこと - hatappi.blog](https://blog.hatappi.me/entry/2017/04/13/201505)
- [ActiveRecord::Persistence#save!](https://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-save-21)
