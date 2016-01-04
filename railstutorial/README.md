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


ローカルサーバを立ち上げる。
```sh
$ rails server
=> Booting WEBrick
=> Rails 4.2.5 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2015-12-27 02:25:34] INFO  WEBrick 1.3.1
[2015-12-27 02:25:34] INFO  ruby 2.1.2 (2014-05-08) [x86_64-darwin14.0]
[2015-12-27 02:25:34] INFO  WEBrick::HTTPServer#start: pid=37251 port=3000
```

## hello world

コントローラのファイルは以下で確認できる。
```sh
$ ls app/controllers/*_controller.rb
app/controllers/application_controller.rb
```

コントローラに`hello`の追加。
```rb
class ApplicationController < ActionController::Base
  # Prevent CSRF attacks by raising an exception.
  # For APIs, you may want to use :null_session instead.
  protect_from_forgery with: :exception

  def hello
    render text: "hello world!"
  end

end
```
合わせて、ルーティングを`config/routes.rb`で設定。
```rb
Rails.application.routes.draw do
  root 'application#hello'

  # The priority is based upon order of creation: first created -> highest priority.
  # See how all your routes lay out with "rake routes".

  # You can have the root of your site routed with "root"
  # root 'welcome#index'

  # Example of regular route:
  #   get 'products/:id' => 'catalog#view'

  # Example of named route that can be invoked with purchase_url(id: product.id)
  #   get 'products/:id/purchase' => 'catalog#purchase', as: :purchase

  # Example resource route (maps HTTP verbs to controller actions automatically):
  #   resources :products

  # Example resource route with options:
  #   resources :products do
  #     member do
  #       get 'short'
  #       post 'toggle'
  #     end
  #
  #     collection do
  #       get 'sold'
  #     end
  #   end

  # Example resource route with sub-resources:
  #   resources :products do
  #     resources :comments, :sales
  #     resource :seller
  #   end

  # Example resource route with more complex sub-resources:
  #   resources :products do
  #     resources :comments
  #     resources :sales do
  #       get 'recent', on: :collection
  #     end
  #   end

  # Example resource route with concerns:
  #   concern :toggleable do
  #     post 'toggle'
  #   end
  #   resources :posts, concerns: :toggleable
  #   resources :photos, concerns: :toggleable

  # Example resource route within a namespace:
  #   namespace :admin do
  #     # Directs /admin/products/* to Admin::ProductsController
  #     # (app/controllers/admin/products_controller.rb)
  #     resources :products
  #   end
end
```


## Vagrant

`vagrant`と`virtualbox`を`homebrew`でインストールする。

```sh
$ brew cask install virtualbox
$ brew cask install vagrant
```

Railsの開発環境を`rails-dev-box`でつくる。

```sh
$ ghq get rails/rails-dev-box
$ cd rails/rails-dev-box
```

VMを起動する。
```sh
$ vagrant up
```

起動がうまくいけば、仮想環境にログインできる。
```sh
$ vagrant ssh
```



## Links

- [Rails tutorial](http://railstutorial.jp/)
- [vagrantで仮想環境を手軽に構築する | dev.wan.co](http://k-shogo.github.io/article/2013/09/25/vagrant/)
- [[Mac] rails-dev-boxで環境構築 - Qiita](http://qiita.com/yamagh/items/b37d21debd2487c50d82)
- [Vagrantの基本 - Qiita](http://qiita.com/kidach1/items/e63c1607705178aa257c)
- [rails/rails-dev-box](https://github.com/rails/rails-dev-box)

