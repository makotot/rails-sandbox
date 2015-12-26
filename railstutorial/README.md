# rails tutorial


## Rails install

```
$ sudo gem install rails
```

`nokogiri`がエラーでインストールできない。

```sh
$ bundle config build.nokogiri --use-system-libraries
$ sudo gem install nokogiri
```
[gem インストール時に発生したエラーとその解決方法まとめ - kzy52's blog](http://kzy52.com/entry/2014/11/09/000511)


```sh
$ sudo gem install rails
```

インストールには成功してるはずだけど

```sh
$ rails -v

  Rails is not currently installed on this system. To get the latest version, simply type:

      $ sudo gem install rails

  You can then rerun your "rails" command.
```

ターミナルを再起動すると解消された。


```sh
$ rails -v

Rails 4.2.5
```

## プロジェクト作成

```sh
$ mkdir helloworld && cd helloworld
$ sudo rails new ./
```

`bundle install`は`rails`が実行しているので不要。


```
Errno::EACCES: Permission denied @ dir_s_mkdir - /Users/username/.rbenv/versions/2.1.2/lib/ruby/gems/2.1.0/extensions/x86_64-darwin-14/2.1.0-static/nokogiri-1.5.10
```
パーミッションエラーが出る。
`.rbenv`ディレクトリのパーミッションを変更して、`rails new`をやり直したらエラーは出なくなる。

```sh
$ sudo chown -R username $HOME/.rbenv
```

[ruby on rails - Errno::EACCESS: Permission denied @ dir_s_mkdir - Stack Overflow](http://stackoverflow.com/questions/30147510/errnoeaccess-permission-denied-dir-s-mkdir)



## Links

- [Rails tutorial](http://railstutorial.jp/)
