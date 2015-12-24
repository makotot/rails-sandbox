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
$ rails new ./
```
`json`がないと言われる。

```sh
An error occurred while installing json (1.8.3), and Bundler cannot continue.
Make sure that `gem install json -v '1.8.3'` succeeds before bundling.
```

```sh
$ sudo gem install json
```


## Links

- [Rails tutorial](http://railstutorial.jp/)
