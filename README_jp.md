# atom-dynamic-macro

* [Dynamic Macro](https://github.com/masui/DynamicMacro)の[Atom](https://atom.io/)実装
* 同じキー操作を2度繰り返した後で`Ctrl-t`を押すと繰り返された操作が再実行されます
 * `abab`と入力した後で`Ctrl-t`を押すと`ababab`になる
 * もう一度`Ctrl-t`を押すと`abababab`になる
 
   ![](https://gyazo.com/2c17e47b7c5f2d917b1c7f6a955f7a90.gif)

### インストール

* `dynamic` `macro`でパッケージ検索してインストール

または
コマンドラインから以下を実行

* `% apm install atom-dynamic-macro`

### 実装

* JunSuzuki氏の[キーボードマクロパッケージ](http://qiita.com/JunSuzukiJapan/items/692dc5390ec545178e7d)を参考にした
* Atomにはキーボードマクロ機能が無いので全部自力でやる必要がある
* `document.addEventListener 'keydown'`でキーダウンイベントを記録しておき、
Ctrl-tが押されたら繰り返しを検出して実行する
* Atomのテンプレート生成器は`package.json`内に以下のような記述を生成し、
キーが押されたときはじめてパッケージがアクティベートされるようになっているが、
Atom起動時に`activate`が呼ばれるようにするために
これを`package.json`から削除している

    ```
    "activationCommands": {
      "atom-workspace": "atom-dynamic-macro:execute"
    },
    ```

### 制限など

* 単純な入力/編集コマンドだけ利用可能
* Ctrl-tに固定されている
