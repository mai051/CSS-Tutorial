これまでも、スタイルを適用する要素を指定するために、要素名やid属性、class属性をセレクターとして記述してきました。実はセレクターでは、いろいろな方法で対象の要素を指定する方法があります。

## 子孫セレクター
HTMLの子孫要素にスタイルを適用するためのセレクターの記述方法です。まずは子孫要素について学んでいきましょう。以下のようなHTMLファイルの場合、

```html
<div>
  <p>子要素</p>
  <div>
    <p>孫要素</P>
  </div>
</div>
```

1行目の`div`要素から見ると、2行目の`p`要素と3行目の`div`要素は子要素、4行目の`p`要素は孫要素となります。ちなみに、3行目の`div`要素から見ると、4行目の`p`要素は子要素となりますが、2行目の`p`要素から見た時には、4行目の`p`要素は子要素にはならないので注意してください。この子要素や孫要素をセレクターで指定することができます。

```css
/* 子要素の指定（子セレクター） */
div > p {
  color: blue;
}

/* 孫セレクターの指定（子孫セレクター） */
div div p {
  color: red;
}
```

`>`を使用することで2行目の子要素である`p`要素にのみスタイルを適用することができます。`>`を使用せずに`div p {}`とした場合は、2行目の子要素と孫要素である4行目の`p`要素の両方にスタイルが適用されます。

- スペースのみで要素を指定した場合

    親要素の中の指定した子孫要素のすべてが指定されます。

- `>`を使用して要素を指定した場合

    親要素の中の指定した子要素のすべてが指定されます。

子要素や孫要素にid属性やclass属性を付与して指定することで、より具体的に要素を指定することも可能です。

## 隣接セレクター
HTMLの隣接している要素を指定してスタイルを適用するためのセレクターの記述方法です。隣接している要素とは、同じ段落にある要素です。

```html
<div>
  <h3>あいさつ</h3>
  <p>お元気ですか？今日のTopicです。</p>
  <ul>
    <li>今日の天気</li>
    <li>明日の天気</li>
    <li>昨日学んだこと</li>
  </ul>
</div>
```

このHTMLでは、`h3`要素に`p`要素が、`p`要素に`ul`要素が隣接しています。`h3`要素の次にある`p`要素を指定する場合は、以下のようにセレクターで指定します。

```css
h3 + p {
  color: green;
}
```

この場合、`p + h3 {}`として`h3`要素を指定することはできません。隣接セレクターでは、あくまで次にある要素を指定するために使用します。

何故こんなややこしい指定の仕方をするの？と疑問に思われるかもしれません。しかし、以下のような構成のWebサイトは少なくありません。もちろん、class属性で指定しても問題ないのですが、「`h3`要素の後の`p`要素には必ずこのスタイルを適用する」と仕様で決まっている場合、隣接セレクターを使用することで、漏れなくスタイルを適用することができます。

```html
<div>
  <h3>The Specialist</h3>
  <p>エンジニア・デザイナーのような職種は、代替可能性を持つ。これは、一定スキルを備えていれば、誰に依頼しても同じということだ。<br />そんな中で、なぜお客様は、“あなたに“依頼するのか？と言える何かを探そう。それは、スキルかもしれないし、スキル以外かもしれない。</p>
  <h3>Professional Team</h3>
  <p>優秀なメンバーがプロフェッショナルなチームを作れたらその可能性は無限大だ。一人ではできないこともチームでならできる。<br />チームのために貢献できることを探そう。君の苦手はメンバーが補ってくれる。だから、君の得意を活かそう。全員の得意を活かすチームを作ろう。</p>
  <h3>Challenge For Pleasure</h3>
  <p>本当の楽しさは、“挑戦の過程”と“挑戦の成果”の両面で実感できる。挑戦すること自体に意味があり、そしてその挑戦の先に、<br />我々が本当に求めている楽しさが存在する。この楽しさは、挑戦した者にしか一生わからない。できないことを恥じる必要はない。挑戦しろ。</p>
</div>
```

![image](https://github.com/user-attachments/assets/e83da664-01cd-496b-8241-3071b7b42ce9)

## CSSを書いてみよう
インプットした内容を基に、早速手を動かして試してみましょう。index.htmlを確認し、指示に従ってCSSを書いてください。まずは自身で書いてみて、わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

index.html

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <link rel="stylesheet" href="styles.css" />
  <title>Document</title>
</head>
<body>
  <div class="header">
    <h1 class="title">CSSハンズオン</h1>
  </div>
  <main>
    <div class="content">
      <article>
        <h2>Part1</h2>
        <p>CSSの基本を知ろう</p>
      </article>
      <article>
        <h2>Part2</h2>
        <p>色やサイズを変更してみよう</p>
      </article>
    </div>
    <div class="side">
      <h3>Part1 CSSの基本を知ろう</h3>
      <p>CSSとは？</p>
      <p>CSSの書き方</p>
      <p>HTMLにCSSを適用する</P>
      <p>CSSを書いてみよう</p>
    </div>
  </main>
</body>
</html>
```

1. class属性`content`の中にある`h2`要素と`p`要素に以下のスタイルを適用してください。
    
    
    |  | 文字サイズ | 文字色 |
    | --- | --- | --- |
    | `h2`要素 | 32px | #6B8E23 |
    | `p`要素 | 20px | #20B2AA |

    <details>
    <summary>回答例</summary>

    ```css
    /* contentクラスの中にあるh2要素とp要素に適用するスタイル */
    .content h2 {
      font-size: 32px;
      color: #6B8E23;
    }
    
    .content p {
      font-size: 20px;
      color: #20B2AA;
    }
    ```
    </details>

2. class属性`side`の中にある`h3`要素の真下にある`p`要素だけ、文字色を赤色にしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* sideクラスの中にあるh3要素直下の要素に適用するスタイル */
    .side h3 + p {
      color: red;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/a813d52e-5b5e-4bd9-8382-e1f2378b0e44)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part4 セレクターを深ぼってみよう"

# リモートリポジトリへプッシュ
git push origin main
```