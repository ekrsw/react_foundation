# Propsを使ってデータを表示する
これまでのところ、`<Header />` コンポーネントを再利用すると、どちらも同じ内容が表示されます。
```index.html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
function HomePage() {
  return (
    <div>
      <Header />
      <Header />
    </div>
  );
}
```
しかし、異なるテキストを渡したい場合や、外部ソースからデータをフェッチしているため事前に情報がわからない場合はどうすればいいのだろうか？

通常のHTML要素には属性があり、その属性を使って要素の動作を変える情報を渡すことができます。例えば、`<img>`要素の`src`属性を変更すると、表示される画像が変わります。`<a>`タグの`href`属性を変更すると、リンク先が変わります。

同じように、情報の断片をプロパティとしてReactコンポーネントに渡すことができる。これを小道具と呼ぶ。例えば、ボタンのバリエーションを考えてみましょう：
<p aling="center">
    <img src="https://github.com/ekrsw/react_foundation/blob/main/asset/06_1_learn-props.jpg"/>
</p>