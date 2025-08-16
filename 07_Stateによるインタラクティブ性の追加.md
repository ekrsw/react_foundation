# Stateによるインタラクティブ性の追加
**State**と**イベントハンドラ**を使って、Reactがどのようにインタラクティビティを追加してくれるのかを探ってみましょう。

例として、`HomePage`コンポーネントの中に「いいね！」ボタンを作ってみましょう。まず、`return()`文の中にbutton要素を追加します：
```index.html
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];
 
  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
      <button>Like</button>
    </div>
  );
}
```
## イベントのリッスン（監視）
ボタンがクリックされたときに何かするようにするには、`onClick`イベントを使います：
```index.html
function HomePage() {
  // ...
  return (
    <div>
      {/* ... */}
      <button onClick={}>Like</button>
    </div>
  );
}
```

