# 問題追加/修正 プルリクエスト

## 必要なものを追加し、いらないものはプルリクエスト時に消すこと

## プルリクエスト発行時確認リスト
- [ ] `challenge.yml`が`challenges/カテゴリ名/問題名/challenge.yml`の場所に置いてある

**challenge.yml**
- [ ] `name`(問題タイトル)にスペースが含まれていない
    - 良い例:Hello_World!, HelloWorld!　ダメな例:Hello World!
- [ ] `description`になにを求めるか書いてある
    - 例:この写真が撮られた場所の郵便番号はなんだろう？
- [ ] `description`にて解答形式について言及している
    - 解答形式: `flag{000-0000}`
- [ ] `auther`が埋まっている
- [ ] `value`は半角数字である
- [ ] 少なくとも1つ以上の`static`形式のフラグがある
    ```yml
    flags:
    - type: static
      content: flag{example_flag_2}
      case_sensitive: false
    ```
- [ ] `Web`など、表記ゆれが考えられない場合は`case_sensitive`を`True`にする
- [ ] `OSINT`のように場所などがそのままフラグになる場合は`regex`(正規表現)形式でのフラグフォーマットも用意する
    ```yml
    flags:
    - type: regex
      content: ^(flag\{)?東京タワー(\})?$ # flag{}は必要ないことを示している
      case_sensitive: false
    ```
- [ ] フラグはフラグフォーマット（`flag{...}`）に準拠している
- [ ] 添付ファイルがある場合は`この問題/files`ディレクトリに配置している
- [ ] `challenge.yml`の`file`に適切にファイルパスを書いている
    ```yml
    files:
    - files/example.bin
    ```
**solution.md**
- [ ] `challenges/カテゴリ名/問題名/solution.md` に解法が記述されている

## レビュアーにしてほしいこと

- [ ] **タイトルを変更している場合は問題が複製されるのでmargeの際、元の問題を消すこと**
- [ ] 問題を解く
- [ ] 問題文について言及
- [ ] 難易度について言及
- [ ] 点数について言及
- [ ] ヒントの点数や有無について言及
- [ ] 解答形式について言及
- [ ] ブラッシュアップが必要か言及

レビュアーは終わったら上をコピーして終わった個所を `[x]` にすること

## 変更点

- 変更点1　
    - なぜ変更したのか
- 変更点2
    - なぜ変更したのか

## 関連Issue

このセクションでは、このPRが関連するIssueやタスクをリンクしてください。以下のように記述します。

- 関連Issue: #123

