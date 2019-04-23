# stepメソッド
``step(limit, step = 1) {|n| ... } -> self
``

selfからはじめstepを足しながらlimitを超えるまでブロックを繰り返します。

```ruby
2.step(10){ |n| puts n }
```
`2`
`3`
`4`
`5`
`6`
`7`
`8`
`9`
`10`

