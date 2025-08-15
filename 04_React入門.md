# React入門
新しく作成したプロジェクトでReactを使用するには、unpkg.comという外部ウェブサイトから2つのReactスクリプトを読み込みます：
- **react**はReactのコア・ライブラリである。
- **react-dom**は、ReactをDOMで使用できるようにするDOM固有のメソッドを提供します。
```index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script type="text/javascript">
      const app = document.getElementById('app');
      const header = document.createElement('h1');
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
      header.appendChild(headerContent);
      app.appendChild(header);
    </script>
  </body>
</html>
```
プレーンなJavaScriptでDOMを直接操作する代わりに、以前に追加したDOMメソッドを削除し、ReactDOM.createRoot()メソッドを追加して特定のDOM要素をターゲットにし、Reactコンポーネントを表示するルートを作成します。次に、root.render()メソッドを追加して、ReactコードをDOMにレンダリングします。
これは、`<h1>`のタイトルを`#app`要素の中にレンダリングするようにReactに指示します。
```index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script>
      const app = document.getElementById('app');
      const root = ReactDOM.createRoot(app);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```
このコードをブラウザで実行しようとすると、構文エラーが発生する：
```terminal
Uncaught SyntaxError: expected expression, got '<'
```
これは、`<h1>...</h1>`が有効なJavascriptではないからです。このコードはJSXです。
## JSXとは何ですか?
JSXはJavaScriptの構文拡張で、使い慣れたHTMLライクな構文でUIを記述できます。JSXの良いところは、3つのJSXルールに従うことを除けば、HTMLとJavaScript以外の新しいシンボルや構文を学ぶ必要がないことです。

しかし、ブラウザは最初からJSXを理解しているわけではないので、BabelのようなJavaScriptコンパイラを使用して、JSXコードを通常のJavaScriptに変換する必要があります。
## プロジェクトにBabelを追加する
プロジェクトにBabelを追加するには、以下のスクリプトを`index.html`ファイルにコピー＆ペーストしてください：
```index.html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```
さらに、スクリプトタイプを`type=text/jsx`に変更することで、変換するコードをバベルに知らせる必要があります。
```index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const domNode = document.getElementById('app');
      const root = ReactDOM.createRoot(domNode);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```
正しく動作していることを確認するには、ブラウザでHTMLファイルを開いてください。

先ほど書いた*宣言的*なReactコードを比較する：
```index.html
<script type="text/jsx">
  const domNode = document.getElementById('app');
  const root = ReactDOM.createRoot(domNode);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```
に、前のセクションで書いたimperative JavaScriptコードを追加する：
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
Reactを使うことで、いかに繰り返しの多いコードを削減できるかがわかるだろう。

Reactは、あなたの代わりにタスク（この場合はUIの更新）を実行するコードの再利用可能なスニペットを含むライブラリだ。
## ReactのためのエッセンシャルJavaScript
JavaScriptとReactを同時に学ぶことは可能だが、JavaScriptに精通していれば、Reactを学ぶプロセスを容易にすることができる。

次のセクションでは、JavaScriptの観点からReactの中核となる概念をいくつか紹介します。ここでは、JavaScriptのトピックについて説明します：

- 関数と矢印関数。
- オブジェクト
- 配列と配列メソッド。
- デストラクチャリング。
- テンプレート・リテラル。
- 三項演算子。
- ESモジュールとインポート/エクスポート構文について

このコースではJavaScriptを深く掘り下げることはしませんが、JavaScriptの最新バージョンに触れておくことは良い練習になります。しかし、まだJavaScriptに習熟していないと感じても、Reactを使ったビルドを始めるのに支障はありません！