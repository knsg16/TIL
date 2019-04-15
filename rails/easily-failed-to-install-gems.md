# インストール時にコケやすいGem
## 一覧
- mysql2
- therubyracer
- libv8
- nokogiri

## 対応方法
### mysql2
macosでは独自のTLSを使用しようとするため、OpenSSLの使用を認めない時がある。
したがって、以下のようなコマンドを打つ必要がある
```linux
bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib --with-cppflags=-I/usr/local/opt/openssl/include"
```

### therubyracer
`v8`をrubyで使えるようにしていくれているGem
libv8と依存関係にあるのでbuild時にv8のバージョンを指定する必要がある。
```linux
bundle config --local build.therubyracer --with-v8-dir=$(brew --prefix v8-315)
```

### libv8
`therubyracer`と依存関係にある。
v8は、GoogleのオープンソースハイパフォーマンスJavaScriptエンジンである。
therubyracerはこのv8をrubyから使えるようにしているgem。

```linux
gem install therubyracer -v '0.12.2' --source 'https://rubygems.org/'
```

参考：

[macOS Mojaveで古いlibv8とtherubyracerが入らない時の対処法](https://qiita.com/shimx/items/32e85093f21e673c7127)

[therubyracer 0.11.0 問題まとめ
](http://suu-g.hateblo.jp/entry/20121222/1356189597)
