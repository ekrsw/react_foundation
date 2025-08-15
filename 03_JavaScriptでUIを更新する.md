# JavascriptでUIを更新する
この章では、JavaScriptとDOMメソッドを使って`h1`タグをプロジェクトに追加するところから、プロジェクトの構築を始めます。

コード・エディターを開き、新しい`index.html`ファイルを作成する。HTMLファイルの中に、以下のコードを追加する：
```index.html
<html>
  <body>
    <div></div>
  </body>
</html>
```
それから、divにユニークなidを与えて、後でターゲットにできるようにします。
```index.html
<html>
  <body>
    <div id="app"></div>
  </body>
</html>
```
HTMLファイル内にJavaScriptを記述するには、`script`タグを追加します：
```index.html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript"></script>
  </body>
</html>
```
さて、`script`タグの中では、`getElementById()`というDOMメソッドを使って、`<div>`要素をidで選択することができます：
```index.html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      const app = document.getElementById('app');
    </script>
  </body>
</html>
```
引き続きDOMメソッドを使って新しい`<h1>`要素を作成することができます：
```index.html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');
 
      // Create a new H1 element
      const header = document.createElement('h1');
 
      // Create a new text node for the H1 element
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
 
      // Append the text to the H1 element
      header.appendChild(headerContent);
 
      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```
すべてが正しく動作していることを確認するために、お好みのブラウザでHTMLファイルを開いてください。
画面に「Develop. Preview. Ship.」と表示された`<h1>`タグが見えるはずです。

## HTMLとDOMの比較
ブラウザ開発者ツール内のDOM要素を見てみると、DOMに`<h1>`要素が含まれていることに気づくでしょう。ページのDOMはソースコード、言い換えれば、あなたが作成したオリジナルのHTMLファイルとは異なります。
<p aling="center">
    <img src="https://github.com/ekrsw/react_foundation/blob/main/asset/03_1_learn-dom-and-source.jpg"/>
</p>
これは、HTMLが最初のページ内容を表しているのに対し、DOMが更新されたページ内容を表しており、あなたが書いたJavaScriptコードによって変更されているからです。

プレーンなJavaScriptでDOMを更新するのは非常に強力ですが、冗長です。あなたは、`<h1>`要素にテキストを追加するためにこのコードを書きました：
```index.html
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```
アプリやチームの規模が大きくなるにつれて、この方法でアプリケーションを構築するのはますます難しくなる可能性がある。

このアプローチでは、開発者はコンピュータに**どのように**すべきかを指示する命令を書くのに多くの時間を費やします。しかし、**何を表示したいか**を記述し、**どのように** DOM を更新するかをコンピュータに考えさせるのは良いことだと思いませんか?
## 命令型プログラミングと宣言型プログラミングの比較
上のコードは**imperative programming.** の良い例です。**どのように**ユーザー インターフェイスを更新するかの手順を書いています。しかし、ユーザー インターフェイスの構築に関しては、開発プロセスをスピードアップできるため、宣言的なアプローチが好まれることがよくあります。DOMメソッドを書く代わりに、開発者が**表示したいもの**を宣言できれば便利です (この場合は、テキストを含む`<h1>`タグです)。

言い換えれば、**命令型プログラミング**は、シェフにピザの作り方を段階的に指示するようなものである。**宣言的プログラミング**は、ピザを作る手順を気にせずにピザを注文するようなものだ。🍕

Reactは、ユーザーインターフェイスを構築するのに使える人気の宣言型ライブラリです。
## React： 宣言型UIライブラリ｜React.com
開発者としては、ユーザーインターフェイスに何を起こしたいかをReactに伝えれば、Reactがあなたの代わりにどのようにDOMを更新するかを考えてくれる。

次のセクションでは、Reactを使い始める方法について説明する。