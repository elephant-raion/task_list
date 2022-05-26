# 目標: 仕事で使えるHTMLとCSSの知識を身につける。

この目標を達成するために、[現状利用されているサイト](https://www.voicemarche.jp/)から自分自身が理解できていない知識を抽出する。
その知識たちがそれぞれどのようなものであるかを理解する。
そして、理解した知識を利用する。

## タスク表

- [x] 自分自身が理解できていない知識を抽出する
  - [x] サイトの大枠を把握する, 見積時間: 30 min., 所要時間:  25 min.
  - [x] 大枠ごとに理解できていない知識を抽出する
    - [x] ヘッダーのところで抽出する, 見積時間: 30 min., 所要時間:  30 min.
      ```css
      .header {
        position: relative; /* 要素が相対的に配置される */
        z-index: 2; /* 2 以下のものは奥側に隠れる */
      }
      ```
      classだけが書かれているhtml tagは何？
    - [x] メインビジュアルのところで抽出する, 見積時間: 30 min., 所要時間: 16 min.
      ```css
      .home-main-visual__wrapper {
        position: relative;
        z-index: 0;
      }
      ```
      blockの組み合わせでよく分からないところがある。
      positionのrelativeとabsoluteの使い分けがちょっとよく分からない。
    - [x] ナビゲーションバーのところで抽出する, 見積時間: 20 min., 所要時間: 15 min.
      dropdown-menuの実装の仕方はよく分からない。
      pcとmobileでの違いはどう取り扱っているのかは、見えない。
    - [x] 新着情報が書かれたところで抽出する, 見積時間: 20 min., 所要時間: 13 min.
      floatを用いて３列のレイアウトを作っている。
      floatを用いたレイアウトの方法はよくわかっていない。
    - [x] 専門カウンセラーを探すところで抽出する, 見積時間: 15 min., 所要時間: 10 min.
    - [x] 人気カウンセラー情報が書かれたところで抽出する, 見積時間: 15 min., 所要時間: 15 min.
    - [x] カウンセリングサービスの特徴が書かれたところで抽出する, 見積時間: 15 min., 所要時間: 13 min.
      ```css
      * {
        box-sizing: border-box;
      }
      .pink-border-xs-button {
        background-clip: padding-box; /* 背景画像の拡張範囲を定める。これはpaddingまでという意味
        */
      }
      ```
    - [x] 使い方が書かれたところで抽出する, 見積時間: 15 min., 所要時間: 5 min.
    - [x] 利用者の声が書かれたところで抽出する, 見積時間: 15 min., 所要時間: 13 min.
      ```css
      element.style {
        position: absolute; /* relative, absoluteで位置を固定する */
      }
      ```
    - [x] 掲載されたメディアが書かれたところで抽出する, 見積時間: 15 min., 所要時間: 6 min.
      全体的に、positionをrelative, absoluteで決めることに慣れていない。
    - [x] 更新情報が書かれたところで抽出する, 見積時間: 10 min., 所要時間: 14 min.
      他のSNSを利用する方法がよくわかっていない。
    - [x] フッター要素で抽出する, 見積時間: 10 min., 所要時間: 4 min.
  - [x] すぐに実現できないことをまとめる, 見積時間: 20 min., 所要時間: 15 min.
    - HTML要素を重ね合わせて表示する。`position: absolute`, `position: relative`, `z-index`を使って。
    - ドロップダウンメニューを作成する。
    - 画像を背景としたHTML要素を作成する。
    - Facebook, TwitterなどのSNSを埋め込む。
    - class名をBEMに従って命名する。
- [x] 不足している知識を利用したページを作成する。
  - [x] 不足している知識を蓄える
    - [x] HTML要素を重ね合わせて表示するための知識を蓄える
      - [x] 概要を知る, 見積時間: 20 min., 所要時間: 19 min.
        `position` propertyにより、要素の配置を設定する。
        - `static`: 要素は通常のフローに従って配置される。`top, right, bottom, left, z-index` propertyの効果はない。
        - `relative`: 
          - 要素は通常のフローに従って、配置される。`top, right, bottom, left`に値が設定されている場合は、その値に応じた相対的オフセットを伴い配置される。そのオフセットは、他の要素の配置に影響を与えない。ページレイアウト内で要素に与えられる空間は、`static`を用いた時と同じである。
          - `z-index`の値が`auto`でない場合、新しい重ね合わせコンテキストを生成する。
        - `absolute`:
          - 要素は通常のフローから除外される。ページレイアウト内に要素のための空間は作成されない。直近の祖先があれば、それに対して相対配置される。そうでないなら、初期の方ガンブロックに対して相対配置される。最終的な配置は、`top, right, bottom, left`の値により決定される。
          - `z-index`の値が`auto`でない場合は、新しい重ね合わせコンテキストを生成する。絶対位置指定ボックスのマージンは、他の要素のマージンと相殺されない。
        - `fixed`: 
          - 要素は通常のフローから除外される。ページレイアウト内に要素のための空間は作成されない。ビューポートによって定められた初期の包含ブロックに対して相対配置される。祖先の１つに`transform, perspective, filter` propertiesのいずれかの値が`none`以外の値に設定されていれば、その場合は祖先が包含ブロックとして振る舞う。最終的な配置は、`top, right, bottom, left`の値によって決定される。
          - 常に新しい重ね合わせコンテキストを作成する。
        - `sticky`:
          - 要素は通常のフローに従って、配置される。直近のスクロールする祖先および包含ブロックに対して`top, right, bottom, left`の値に基づいて相対配置される。オフセットは他の要素の配置には影響を与えない。
          - 常に新しい重ね合わせコンテキストを生成する。直近の祖先がスクロールしない場合でも、スクロールの仕組みをもつ直近の祖先に粘着する。
      - [x] ドキュメント上でよく分からなかったことを調べる, 見積時間: 20 min., 所要時間: 18 min.
        - 重ね合わせコンテキスト(Stacking context): HTML要素の３次元の概念。ユーザに関係のある仮想的なz軸にそったもの。その要素の属性に基づいて、HTML空間を優先度付きの順序で描画する。
          - 重要：子要素の`z-index`の値は、その親要素に対してのみ意味を持つ。
        - 包含ブロック(containing block): 要素から見て直近のブロックレベルの祖先のコンテンツ領域。
          - 要素の寸法と位置は、包含ブロックに影響される。`width, height, padding, margin`に適用されるpercent値、絶対位置指定要素のoffset propertyは、要素の包含ブロックから計算される。
      - [x] 詳細を知る, 見積時間: 30 min., 所要時間: 23 min.
        位置の種類
        - 位置指定要素: `position`の計算値が`relative, absolute, fixed, sticky`のいずれかである要素。つまり、`static`以外の全て。
        - 相対位置指定要素: `position`の計算値が`reletive`である要素。垂直方向は`top, bottom`で、水平方向は`left, right`で指定する。
        - 絶対位置指定要素: `position`の計算値が`absolute, fixed`である要素。`top, right, bottom, left`の各propertyは、この要素の包含ブロックの端からのoffsetを指定する。
        - 粘着位置指定要素: `position`の計算値が`sticky`である要素。包含ブロックがフロールート内で指定された閾値を達するまでは相対的な配置として扱われる。包含ブロックの反対の端が来るまでその位置に粘着するものとして扱われる。
    - [x] ドロップダウンメニューを作成するための知識を蓄える 見積時間: 20 min., 所要時間: 18 min.
      Dropdown menuは、切り替え可能なメニューである。それはユーザに事前定義されたリストから、値を１つ選ぶことを許可する。
      - Hoverable Dropdown: userが要素の上にマウスを乗せたときに現れるdropdown menu
        ```html
        <div class="dropdown">
          <button class="dropbtn">Dropdown</button>
          <div class="dropdown-content">
            <a href="#">Link 1</a>
            <a href="#">Link 2</a>
            <a href="#">Link 3</a>
          </div>
        </div>
        ```
        `.dropdown` classは`position: relative`を使う。それは、dropdown contentをdropdown buttonの下に配置するために使っている。dropdown contentをそのbuttonの下に表示させるために、`position: absolute`を使う。
        ```css
        .dropbtn {
          background-color: #04A6D;
          color: white;
          padding: 16px;
          font-size: 16px;
          border: none;
        }

        .dropdown {
          position: relative;
          display: inline-block;
        }

        .dropdown-content {
          display: none;
          position: absolute;
          background-color: #f1f1f1;
          min-width: 160px;
          box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
          z-index: 1;
        }

        .dropdown-content a {
          color: black;
          padding: 12px 16px;
          text-decoration: none;
          display: black;
        }

        .dropdown-content a:hover {
          background-color: #ddd;
        }

        .dropdown:hover .dropdown-content {
          display: block;
        }

        .dropdown:hover .dropbtn {
          background-color: #3e8341;
        }
        ```
      - Click Dropdowns
    - [x] 画像を背景としたHTML要素を作成するための知識を蓄える 見積時間: 20 min., 所要時間: 12 min.
      `background-image` propertyは、要素に１つ以上の背景画像を設定する。
      始めに指定した画像が前面に描画される。
      ```css
      background-image: url("./img/star.png"), url("./img/lizard.png");
      ```
      要素のborderは背景画像より上に描画される。
      `background-color`は背景画像より下に描画される。
      画像がボックスとそのborderに対してどのように描画されるかは、`background-clip, background-origin`で定義される。
      画像が描画できない場合は、`none`を指定しているように振る舞う。

      `background-clip`は、要素の背景はどこまで拡張するのかを指定する。
      `background-origin`は、背景配置領域の開始位置を定める。
    - [x] Facebook, TwitterなどのSNSを埋め込むための知識を蓄える 見積時間: 20 min., 所要時間: 17 min.
      - [Facebook](https://developers.facebook.com/docs/plugins/page-plugin?locale=ja_JP)
      - [Twitter](https://publish.twitter.com/#)
    - [x] class名をBEMに従って命名するための知識を蓄える
      - [x] BEMに従ってclass名をつけるプラクティスを探す, 見積時間: 30 min., 所要時間: 7 min.
      - [x] [BEM 101](https://css-tricks.com/bem-101/)を読む, 見積時間: 30 min., 所要時間: 35 min.
        BEMは、HTMLとCSSの間の関係を理解しやすくするための命名規約である。
        ```css
        .btn {} /* Block component */
        .btn__price {} /* そのblockに依存する要素 */
        .btn--orange {} /* blockのstyleを変更するもの */
        .btn--big {}
        ```
        - Block: 新しいcomponentのtop-levelの抽象物;`.btn { }`。親として考えられるもの。
        - Element: blockの子供。blockの中に配置される。次のように定義される; `.btn__price { }`
        - Modifier: blockを操作するもの。特定componentのスタイルやテーマを変更する。`btn--orange`
        ```html
        <a class="btn btn--big btn--orange" href="https://css-tricks.com">
          <span class="btn__price">$9.99</span>
          <span class="btn__text">Subscribe</span>
        </a>
        ```
        classには１つの責任を持たせる。
        ```html
        <a href="https://css-tricks.com" class="btn">
          <span class="btn__text">Standard button</span>
        </a>

        <a href="https://css-tricks.com" class="btn btn--orange btn--big">
          <span class="btn__price">$3</span>
          <span class="btn__text">Big button</span>
        </a>

        <a href="https://css-tricks.com" class="btn btn--blue btn--big">
          <span class="btn__price">$4</span>
          <span class="btn__text">Big button</span>
        </a>

        <a href="https://css-tricks.com" class="btn btn--green btn--big">
          <span class="btn__price">$9</span>
          <span class="btn__text">Big button</span>
        </a>
        ```
        ```css
        /* Block */
        .btn {
          text-decoration: none;
          background-color: white;
          color: #888;
          border-radius: 5px;
          display: inline-block;
          margin: 10px;
          font-size: 18px;
          text-transform: uppercase;
          font-weight: 600;
          padding: 10px 5px;
        }

        /* Element */
        .btn__price {
          background-color: white;
          color: #fff;
          padding-right: 12px;
          padding-left: 12px;
          margin-right: -10px; /* realign button text padding */
          font-weight: 600;
          background-color: #333;
          opacity: .4;
          border-radius: 5px 0 0 5px;
        }

        /* Element */
        .btn__text {
          padding: 0 10px;
          border-radius: 0 5px 5px 0;
        }

        /* Modifier */
        .btn--big {
          font-size: 28px;
          padding: 10px;
          font-weight: 400;
        }

        /* Modifier */
        .btn--blue {
          border-color: #0074D9;
          color: white;
          background-color: #0074D9;
        }

        /* Modifier */
        .btn--orange {
          border-color: #FF4136;
          color: white;
          background-color: #FF4136;
        }

        /* Modifier */
        .btn--green {
          border-color: #3D9970;
          color: white;
          background-color: #3D9970;
        }


        body {
          font-family: "fira-sans-2", sans-serif;
          background-color: #ccc;
        }
        ```
        なぜBEMを考えるのか？
        1. componentの新しいsytleを作りたいなら、どのmodifiers and childrenが既に存在しているかを感じることができる。
          書く必要がないCSSを識別できる。なぜなら、それを一目で見分けることができるから。
        2. CSSの代わりにmarkupを読んでいるなら、素早く考えを得られるべきである。その要素に関係あるものの考え。
        3. Designers and developersでcomponentの名前は一貫性を持たせたほうがいい。BEMはteam memberに宣言的なsyntaxを与える。

        全てがclassであり、ネストはなくすといい。
        - [x] [BEM 101](https://css-tricks.com/bem-101/)の問題部分を読む, 見積時間: 40 min., 所要時間: 29 min.
          以下のように書いてしまったら、メンテナンスしにくい。
          ```css
          .nav .nav__listItem .btn--orange {
            background-color: green;
          }
          ```
          block(`.nav`)は、他のblock or modifier(`.btn--orange`)のスタイルをオーバーライドすべきではない。
          一方で、これは、それをほとんど不可能にする。HTMLを読むこと and このcomponentがすることを理解すること。
          そのprocess内で、私たちは結ばれる。codebase内でもう一つの開発者の信頼を共有するために。
          これはHTMLに向かう。あなたが期待することは何か？あなたが次のmarkupを見たかどうかを期待する？
          ```html
          <a class="btn" href="https://css-tricks.com">
            <div class="nav__listItem">Item one</div>
            <div class="nav__listItem">Item two</div>
          </a>
          ```
          ここに行くことは、無関係なblock内の要素はcodeを持つことである。開発者が必要とするcode。
          しかし、子要素は `.nav` classを要求しない。`.nav`要素を親として。
          これは例外な混乱と一致しないcodebaseを作る。これは避けるべきである。
          この問題を次のように要約できる。
          1. 無関係なblock内のmodifiersはオーバーライドすべきではない。
          2. 不必要な親要素を作ることを避けるべきである。その子供はとても幸せに存在するとき。
  - [x] ページのモックアップを作成する, 見積時間: 30 min., 所要時間: 15 min.
  - [x] 画像の上にテキストを載せたメインビジュアルを作る, 見積時間: 20 min., 所要時間: 18 min.
  - [x] ドロップダウン メニューを作る, 見積時間: 20 min., 所要時間: 15 min.
  - [x] 記事コンテンツを作成する（背景画像つき）, 見積時間: 20 min., 所要時間: 15 min.
  - [x] FacebookとTwitterのプラグインを挿入する, 見積時間: 20 min., 所要時間: 15 min.
- [ ] 画面のレイアウトを実験できるRailsアプリを作成する(HamlとSassが使える)
  - [x] local環境にRails 7をインストールする, 見積時間: 30 min., 所要時間: 22 min.
  - [x] そのアプリのためのremote repositoryを作成し、そのcloneをlocalに作成する, 見積時間: 15 min., 所要時間: 12 min.
  - [x] Sassの基礎を知る, 見積時間: 30 min., 所要時間: 25 min.
  - [x] RailsでSassを使えるようにする, 見積時間: 30 min., 所要時間: 42 min.
  - [x] RailsでHamlを使えるようにする, 見積時間: 20 min., 所要時間: 10 min.
  - [x] 不足している知識を利用したページをRailsアプリに備え付ける
    - [x] experiment01_controllerを作成する。`rails g controller experiment01 index`, 見積時間: 5 min., 所要時間: 2 min.
    - [x] HTMLをHAML化する
      - [x] imageを出力する方法を調べる, 見積時間: 15 min., 所要時間: 10 min.
      - [x] main-visual blockをHAML化する, 見積時間: 15 min., 所要時間:  5 min.
      - [x] dropdown blockをHAML化する, 見積時間: 15 min., 所要時間:  15 min.
      - [x] article blockをHAML化する, 見積時間: 15 min., 所要時間: 6 min.
      - [x] sns blockをHAML化する, 見積時間: 15 min., 所要時間: 6 min.