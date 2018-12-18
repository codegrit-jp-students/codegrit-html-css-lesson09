# HTMLフォーム

## 目的

- フォームの基本的な作成方法を学ぶ
- フォームの仕組みを理解する
- フォームの各要素のスタイリング方法を学ぶ

## はじめに

サイトへのユーザー登録や、お問合せなどウェブを利用していると多くの場面でHTMLフォームを利用する場面があります。今回のレッスンではこのHTMLフォームを自分で作成する方法、またデザインのカスタマイズ方法、裏側では何が起っているのかなどフォームの基本を説明していきます。

## フォームの作成方法

HTMLフォームを作成するには`form`要素を利用します。

```html
<form>
  ...
</form>
```

## label要素

ラベルは、入力する項目が何かをユーザーに示すために利用します。例えば、ユーザー登録フォームの多くではメールアドレスを要求します。この場合、以下の例のように書きます。

```html
<label for="email">メールアドレス</label>
```

セマンティクスHTMLでは上記の例のように`for`属性を利用して、そのラベルがメールアドレスのためであることを明示することが推奨されています。`for`には任意の値を与えることが出来ますので`for=mail`、`for=first-name`、`for=password`など分かりやすい名前を入力しましょう。

## input要素

フォームではユーザーにテキストを入力してもらったり、複数の選択肢から一つを選んでもらうなどしてもらいますが、この時に`textarea`要素など独自の要素を使う場合と、`<input>`要素を利用し、type属性でフォームのタイプを変更する場合との2つがあります。`input`要素のシンタックスは以下の通りです。

```html
<input type="type" ...>
```

## テキストインプット

input要素の中で最もよく使うのがテキストインプットです。例えば、ユーザーに名前を入力してもらいたい場合は以下のように書きます。

```html
<label for="name">名前</label>
<input type="text" name="name">
```

![テキストインプット1](./images/text-input.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/text-input1.html)

### type属性

上記の例で、type属性には`"text"`と入っています。テキストを入力するタイプのinput要素のtype属性にはこの他にも、以下のようなものがあります。セマンティクスHTMLでは、フォーム入力情報の種類に併せて適切な`type`属性を指定することを推奨しています。

- password: パスワード入力欄に利用します。。ほとんどのブラウザでは`type="password"`が指定されている場合、入力情報を`*`へと変換してくれます。
- email: メールアドレス入力欄に利用します。
- search: 検索用テキストの入力欄に利用します。
- url: URLの入力欄に利用します。
- tel: 電話番号の入力欄に利用します。

### placeholder属性

フォームを入力する際に、入力欄の中に注意書きなどを書きたい場合があります。例えばパスワードでよくあるのが、一定文字以上の入力が必要だったり、記号を必須とするケースです。こうした時には`placeholder属性`を利用します。

```html
<label for="password">パスワード</label>
<input type="password" name="name" placeholder="英数字記号8文字以上で入力して下さい">
```

![placeholder属性](./images/placeholder2.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/text-input2.html)

上記の画像のようにInput欄の長さを調整しないと途中で切れてしまうので注意してください。

### name属性

フォームで入力されたデータが何を示すのかを判断するために`name属性`が必要です。`label`要素の`for`属性同様に任意の名前を付けられます。

## テキストエリア要素

テキストエリア要素は、文章を入力するために利用します。よく使うのはユーザーにプロフィールを入力してもらう時や、お問合せフォームの内容を書いてもらうときです。input要素とは異なり終了タグが必要ですので注意して下さい。input要素と同様に`placeholder属性`を設定することが可能です。

```html
<label for="bio">プロフィール</label>
<textarea name="bio" placeholder="プロフィールを入力して下さい。"></textarea>
```

![テキストエリア要素](./images/textarea1.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/textarea.html)

## チェックボックス

`input`要素の`type`属性に"checkbox"を指定することでチェックボックスを作成出来ます。

チェックボックスが使われるパターンは2つあります、1つは利用規約への同意やメルマガ配信希望への同意など、1つの質問に対してオン、オフを選んでもらいたい場合です。もう一つは一つの質問に対して複数の選択肢の中から当てはまるものを全て選んで欲しい場合です。以下に2つのパターンそれぞれ例を挙げます。

1. 1つの質問に対して利用する場合

```html
<input type="checkbox" name="terms"><label for="terms">利用規約へ同意する</label>
```

![チェックボックス1](./images/checkbox1.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/checkbox1.html)

2. 複数の選択肢で当てはまるもの全て選択

```html
<p>プログラミングを学ぶ動機を教えてください(複数選択可)</p>
<input type="checkbox" name="reasons" id="service"><label for="service">自分のサービスを作成するため</label>
<input type="checkbox" name="reasons" id="job"><label for="job">エンジニアとして就職/転職するため</label>
<input type="checkbox" name="reasons" id="communication"><label for="communication">エンジニアと対等にコミュニケーショを取るため</label>
...
```

![チェックボックス2](./images/checkbox2.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/checkbox2.html)

 さて上記の複数選択の例では、`name`属性と`id`属性の2つを利用しました。`name`には、reasonsと入れて、他の選択肢が同じ質問に対するチェックボックスであることを明確にしています。加えてid属性を利用してそれぞれの項目の内容を明確にしています。

## ラジオボタン

`input`要素の`type`属性に"radio"を指定することでチェックボックスを作成出来ます。  ラジオボタンは複数選択肢の中から一つだけを選択肢てもらいたい場合に利用します。以下はユーザーの年代を知りたい場合の例です。

```html
<p>年齢層を選択して下さい</p>
<input type="radio" name="age-group" id="age-10s"><label for="age-10s">10代</label>
<input type="radio" name="age-group" id="age-20s"><label for="age-20s">20代</label>
<label for="age-30s">30代</label>
<input type="radio" name="age-group"id="age-40s">
<label for="age-30s">40代</label>
...
```

![ラジオボタン1](./images/radio1.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/radio1.html)

## セレクト

`select`属性を利用することでセレクトを作成出来ます。セレクトは複数選択肢の中から一つを選んで貰いたい場合に利用します。ラジオボタンと同一の利用方法です。では、どう使い分けるのかというと、セレクトフォームは複数の選択肢を1行に全部含めたい場合や選択肢の数が多く、全部をラジオボタンで書くと冗長になってしまう場合に使います。よく使う場面は例えば出身国や県を選んでもらいたい場合です。選択肢を作成するには`option`要素を利用します。

以下に例を挙げます。

```html
<p>居住国を選んで下さい。</p>
<select name="country">
  <option value="japan">日本</option>
  <option value="usa">アメリカ合衆国</option>
  <option value="canada">カナダ</option>
  <option value="china">中国</option>
  ...
</select>
```

![セレクト1](./images/select1.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/blob/master/select1.html)

さて、ここで注目をしていただきたいのは、`value`属性です。この属性はフォームを提出する際にどのオプションが選ばれたのかを知るために利用します。このvalueは、セレクトだけではなく、他の`input`要素などでも利用するので、後ほど「フォーム提出の仕組み」の項目で詳しく説明していきます。

## 提出ボタン

フォームに情報を入力してもらった後、最終的にユーザーにそのデータを提出してもらう必要があります。この時に多くの場合ボタンを利用します。`form`要素の中で使われるボタンには他の要素と同様に`type`属性を指定します。この`type`属性には以下の3つが入ります。

- submit: 一般的に使われるのが`submit`です。フォームデータを送信するために利用します。
- reset: リセットボタンはフォームの入力内容をリセットするために利用します。以前はよく使われていましたが、最近では提出ボタンと誤ってクリックするケースを避けるため使わないことが多いです。
- button: このタイプのボタンは何もしません。このボタンはボタンとJavascriptとを連動させて連動させて何かを行いたい場合に利用します。

```html
<button type="submit">登録する</button>
```

## フォーム提出の仕組み

さて、ここまでHTMLフォームを作成する方法を説明してきました。ではフォームを提出した時には裏側では何が起っているのでしょうか。ここではその仕組について詳しく見ていきましょう。

### 1. ブラウザからサーバーにデータを送信

フォームを提出するとフォームに入力されたデータがインターネットを通じてサーバー上のあるURLへと送信されます。

![フォーム提出の仕組み1](./images/how-form-works-1.png)

### 2. サーバー側でフォームのデータを処理

サーバー側では例えば、ユーザー登録であれば同じ名前で登録されたユーザーはいないかのチェックなど様々な処理を行います。

![フォーム提出の仕組み2](./images/how-form-works-2.png)

### 3. 必要ならデータを保存する

サーバー側でデータを処理した後、必要であればそのデータをデータベースに保存します。

![フォーム提出の仕組み3](./images/how-form-works-3.png)

### 4. サーバーからブラウザに結果を返す

無事に処理が完了した際には成功を意味する`200`というコードを返し、処理が失敗してしまったときはエラーの内容を意味するエラーコード(例えば`404`はページが見つからないことを意味する)を返します。

![フォーム提出の仕組み4](./images/how-form-works-4.png)

### 5. ブラウザで結果を表示

例えば、成功だったら「ユーザー登録ありがとうございます」というような表示を行い、失敗なら「エラーが発生しました」と表示します。

![フォーム提出の仕組み5](./images/how-form-works-5.png)

## データの送信

### form要素のaction属性とmethod属性

フォームの提出ボタンをクリックした時にブラウザではどのようなデータをどこに送信するのか、また送信は何のために行うのかを知っている必要があります。このどこに送信するかと、何のために送信するのかは、form要素の`action`属性と`method`属性に定義します。

```html
<form action="https://www.example2.com/users/create" method="post">
...
</form>
```

### action属性

action属性には、送信先のURLを指定します。

### method属性

method属性には`post`、`get`のいずれかのメソッドを指定します。postの場合はデータを保存したい時、getの場合はデータを取得したい時に利用します。

### 送信されるデータ

データは各インプットのnameを基に送信されます。例えば以下のフォームを考えてみましょう。

```html
<form action="/somewhere" method="post">
  <div>
    <label for="name">名前</lable>
    <input type="text" name="user-name">
  </div>
  <div>
    <label for="email">メールアドレス</label>
    <iput type="email" name="user-email">
  </div>
</form>
```

すると送信時には、以下のように情報が送信されます。

```
user-name="入力された名前"
user-email="入力されたメールアドレス"
```

## fieldset要素とlegend要素

さて、上記の送信されるデータの例では、各inputを

`div`要素で囲みました。しかしセマンティクスHTMLではここに`fieldset`要素を利用します。また、`label`属性には単語のみを書きますが、より長く項目の説明を書きたい場合`legend要素`を利用することが出来ます。以下に例を挙げます。


```html
<form action="/somewhere" method="post">
  <fieldset>
    <legend>名前を全角で入力してください。</legend>
    <label for="name">名前</lable>
    <input type="text" name="user-name">;
  </fieldset>
  <fieldset>
    <legend>;よく使うメールアドレスを入力して下さい。</legend>;
    <label for="email">;メールアドレス</label>;
    <iput type="email" name="user-email">;
  </fieldset>;
</form>
```

## フォームのスタイリング

フォームをCSSでスタイリングするにはこれまでと少し違ったテクニックが必要になります。

### input要素をタイプごとにスタイリングする

input要素にはこれまで見たとおりemail、password、checkboxなど様々なタイプがあります。こうしたそれぞれのtypeについてスタイリングを変更したい場合には以下のようにします。

例えば、以下はtype属性が"email"のときのスタイリング例です。

```css
input[type=email] {
  color: red;
}
```

このようにCSSでは

```css
セレクター[<属性>=<値>] {
  ...
}
```

というように、属性を指定に利用することが出来ます。

フォームのスタイリングではこの属性を利用した指定を多く使うことになります。

### placeholderをスタイリングする

placeholderをスタイリングしたい場合には以下のように書きます。


```css
input[type=text]::-webkit-input-placeholder {
  color: red;
}
input[type=text]::-moz-placeholder {
  color: red;
}
```

```html
<form>
  <label for="name">;名前</label>;
  <input type="text" placeholder="名前を入力してください">;
</form>
```

すると次のようにplaceholderが赤色で表示されます。

![placeholderスタイリング例](./images/placeholder.png)

[サンプルコード](https://github.com/codegrit-jp-students/codegrit-html-css-lesson09-samples/tree/master/placeholder-styling)

## チャレンジ

[チャレンジ9](./challenge/README.md)


## 更に学ぼう

### 記事で学ぶ

- [初めてのHTMLフォーム - MDN](https://developer.mozilla.org/ja/docs/Learn/HTML/Forms/Your_first_HTML_form)

- [HTML5でフォームを大幅に改良 - HTML5 Rock](https://www.html5rocks.com/ja/tutorials/forms/html5forms/)

### 動画で学ぶ

- [formタグでフォームを作ろう - ドットインストール](https://dotinstall.com/lessons/basic_html_v3/31617)
