# 開発環境を構築する

## タスクばらし

- 大まかなタスクにばらす, 見積時間: 30 min., 所要時間: 21 min.
- [generatorにより余計なfileが生成されないようにする]タスクをばらす, 見積時間: 15 min., 所要時間: 2 min.
- [DBの環境を整える]タスクをばらす, 見積時間: 15 min., 所要時間: 20 min.
- [Template engineをhamlに変更する]タスクをばらす, 見積時間: min., 所要時間: min.
- [Static assetをwebpackerで管理する]タスクをばらす, 見積時間: min., 所要時間: min.
- [Bootstrapを導入する]タスクをばらす, 見積時間: min., 所要時間: min.
- [Test環境を整える]タスクをばらす, 見積時間: min., 所要時間: min.
- [Lintを導入する]タスクをばらす, 見積時間: min., 所要時間: min.
- [Herokuに本番環境を作る]タスクをばらす, 見積時間: min., 所要時間: min.

## 調査

- railsのgeneratorの設定方法を調べる, 見積時間: 30 min., 所要時間: 5 min.
- railsでpostgresqlを使う方法を調べる, 見積時間: 5 min., 所要時間: 3 min.
- Template engineをhamlにする方法を調べる, 見積時間: 5 min., 所要時間: 3 min.

## 実装

- Projectを作成する, 見積時間: 5 min., 所要時間: 5 min.
  `rails new miniblog -d postgresql --skip-test-unit --skip-test`
  - 上記で作成したprojectのremote repositoryを設定する
    - GitHubでminiblogという名前のrepositoryを作成する
    - GitHub上の手順に従って、miniblog repositoryを上記projectのremote repositoryとする
- 不要なgemを取り除く, 見積時間: 3 min., 所要時間: 1 min.
  - `jbuilder` gemを`Gemfile`から取り除く
- generatorにより余計なfileが生成されないようにする, 見積時間: 3 min., 所要時間: 3 min.
  - `config/application.rb`に、以下を加える
  ```ruby
  config.generators do |g|
    g.assets false
    g.helper false
  end
  ```
- DBの環境を整える, 見積時間: 30 min., 所要時間: 7 min.
  - `config/database.yml`に以下を加える
  ```yml
  default: &default
    username: miniblog
    password: 
    host: localhost
  ```
  - `config/database.yml`から`production`のところを削除する
  - PostgreSQL DBに、`miniblog`という名前のユーザを作成する
    `createuser miniblog`
  - 開発とテストの両方のDBを作成する
  ```
  createdb miniblog_development -O miniblog
  createdb miniblog_test -O miniblog
  ```
  - `config/database.yml`をコピーして、`config/database.yml.sample`を作る
  - `config/database.yml`をGitの管理外にする
    - `.gitignore`に、`/config/database.yml`を加える
  - `rails s`を実行して、DBにアクセスできていることを確かめる
- Template engineをhamlに変更する, 見積時間: min., 所要時間: min.
  - `haml-rails` gemを`Gemfile`に加えて、`bundle install`する
  - `rails haml:erb2html`を実行して、erb fileをhaml fileに変換する
- Static assetをwebpackerで管理する, 見積時間: min., 所要時間: min.
  - `app/assets/stylesheets/application.css`を削除する
  - `app/javascript`に`stylesheets`, `images` directoryを作成する
  - `stylesheets` directoryに、`application.scss`を作成する
  - `app/javascript/packs/application.js`に、以下を加える
    `import '../stylesheets/application.scss'`
- Bootstrapを導入する, 見積時間: min., 所要時間: min.
  - Bootstrap5をinstallする
    `yarn add bootstrap`
  - `app/javascript/stylesheets/application.scss`に、以下を加える
  - `app/javascript/packs/application.js`に、以下を加える
  - `app/views/layouts/application.html.haml`の`stylesheet_link_tag`を`stylesheet_pack_tag`に置き換える
- Test環境を整える, 見積時間: min., 所要時間: min.
  - `rspec-rails`, `factory_bot_rails` gemを`Gemfile`に加え、`bundle install`する。ただし、groupは、`:development, :test`である
  - `config/application.rb`に、以下を加える。
  ```ruby
  config.generators do |g|
    g.test_framework :rspec,
      view_specs: false,
      helper_specs: false,
      routing_specs: false,
      request_specs: false,
      controller_specs: false
  end
  ```
- Lintを導入する, 見積時間: min., 所要時間: min.
  - 以下を実行して、指摘されたところを直す
    `bundle exec rubocop`
  - 以下を実行して、指摘されたところを直す
    `bundle exec haml-lint app/views`
- Herokuに本番環境を作る



