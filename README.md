# ctfd-auto-deploy

## プロジェクト構造
```
ctfd-deployment
├── .github
│   └── workflows
│       └── deploy_challenges.yml    # デプロイメント用のGitHub Actionsワークフロー
├── challenges
│   ├── category1
│   │   └── challenge1
│   │       ├── challenge.yml        # チャレンジ1の設定
│   │       └── files
│   │           └── example.png      # チャレンジ1用の画像ファイル
│   └── category2
│       ├── challenge2
│       │   ├── challenge.yml        # チャレンジ2の設定
│       │   └── files
│       │       └── example.bin      # チャレンジ2用のバイナリファイル
│       └── challenge3
│           └── challenge.yml        # チャレンジ3の設定
│                                    # filesはなくても大丈夫
│
├── config.ini                       # デプロイメントの設定
├── requirements.txt                 # プロジェクトのPython依存関係
├── pull_request_template.md         # プルリクの際
└── README.md                        # プロジェクトのドキュメント
```

## 管理者が最初のみやること

GitHub actionsのシークレットにCTFdのURLとアクセストークンを追加します。
1. まずCTFdにAdminアカウントでログイン
2. プロフィール/アクセストークンからアクセストークンを作成
3. それを`https://github.com/username/repo-name/settings/secrets/actions`に登録

この命名ミスると動かないので注意
- CTFD_ACCESS_TOKEN 
```
ctfd_xxxxxxxxx~
```
- CTFD_URL
```
http://hoge.example.com
```

## 始め方
このプロジェクトを始めるには、以下の手順に従ってください：

1. リポジトリのクローン: 以下のコマンドを使用してこのリポジトリをローカルマシンにクローンします：
```
git clone https://github.com/hatomato0920/ctfd-auto-deploy.git
```

2. チャレンジの準備
   1. challengesディレクトリの中からカテゴリを選びます。(ない場合は作成します。)
      - 例: `challenges/OSINT`
   2. カテゴリディレクトリの中に問題のディレクトリを追加します。
      - 例: `challenges/OSINT/Fastest_Car`
   3. 問題ディレクトリにカテゴリディレクトリの`challenge.yml`(OSINT/challenge.ymlなど)を追加します。
   4. 添付するファイルがある場合は問題ディレクトリの中にfilesディレクトリを作成し、`challenge.yml`の`files:`にパスを追加します。
      - 例: `Fastest_Car/files/Car.png`

3. チャレンジのデプロイ: デプロイメントスクリプトを実行して、チャレンジをCTFdプラットフォームにアップロードします。

## challenge.ymlについて

- `challenge.yml`は`.yaml`でも動くようにしているとは思いますが保証はできません！
   - カテゴリにおいてある`challenge.yml`をコピーすることを想定しているので不具合はあまり起こらないとは思います。
- `challenge/**/*.y*ml`の場所以外の`.y*ml`は検出しません。カテゴリにコピー用の`challenge.yml`を置くことで簡単に問題の`challenge.yml`を追加できます。
   - testディレクトリをそのままコピーして編集してもOK