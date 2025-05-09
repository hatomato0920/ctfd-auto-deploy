# ctfd-auto-deploy

## 📦 プロジェクト構造
```
ctfd-auto-deploy
├── .github
│   └── workflows
│       ├── deploy_challenges.yml    # GitHub Actionsワークフロー
│       └── lint_challeges.yml       # 問題形式チェック
├── challenges
│   ├── category1
│   │   └── challenge1
│   │       ├── challenge.yml        # 問題設定ファイル
│   │       └── files/
│   │           └── example.png      # 添付ファイル
│   └── category2
│       ├── challenge2/
│       └── challenge3/
│           └── challenge.yml
|
├── requirements.txt                 # Python依存関係
├── pull_request_template.md         # PRテンプレート
└── README.md
```

---

## 🔐 管理者が最初にやること（1回だけ）

### GitHub Secrets の登録

1. 管理用CTFdに **Adminアカウント** でログイン  
2. プロフィール → アクセストークン を発行  
3. GitHub の Secrets に以下を登録  
   → `https://github.com/ユーザー名/リポジトリ名/settings/secrets/actions`

| Secret名            | 説明 |
|--------------------|------|
| `CTFD_URL`         | CTFdのURL（例: `https://ctf.example.com`） |
| `CTFD_ACCESS_TOKEN`| Admin APIトークン（例: `ctfd_abc123...`） |

> ⚠️ **名前のスペルミスに注意！** → 正しくないとCIが失敗します。

---

## 🚀 始め方（利用者向け）

### 1. リポジトリをフォークする

> このリポジトリは**自分の問題を追加・管理する前提**です。Forkしてから使いましょう。

1. GitHub右上の「Fork」ボタンをクリック  
2. 自分のアカウントにコピーされたらクローンします：

```
git clone https://github.com/あなたのユーザー名/ctfd-auto-deploy.git
cd ctfd-auto-deploy
```

3. GitHub Secrets に以下を登録（管理者手順参照）  
   - `CTFD_URL`  
   - `CTFD_ACCESS_TOKEN`

---

### 2. チャレンジを追加する

1. `challenges/` の中からカテゴリを選ぶ（なければ作成）  
   例: `challenges/OSINT`

2. カテゴリディレクトリ内に問題用ディレクトリを作成  
   例: `challenges/OSINT/Fastest_Car`

3. `challenge.yml` を追加  
   例: `challenges/OSINT/Fastest_Car/challenge.yml`  
   → カテゴリ直下のテンプレ `challenge.yml` をコピーすると楽です

4. 添付ファイルがある場合は `files/` を作って、`challenge.yml` の `files:` にパスを指定  
   例: `Fastest_Car/files/Car.png`

---

### 3. デプロイする

- GitHub Actions が push/pull request をトリガーに自動で CTFd にアップロードします

---

## 📝 `challenge.yml` について

- `.yml` も `.yaml` も動くとは思いますが、`.yml`を推奨（動作保証外の挙動が起こる可能性あり）  
- `challenges/**/challenge.yml` の階層以外は無視されるので、正しい構造に注意  
- カテゴリ直下にテンプレとして `challenge.yml` を置いておくと問題作成が楽になる  
- 例：`challenges/OSINT/challenge.yml` → `challenges/OSINT/Fastest_Car/` にコピーして編集  

---

## ✅ 補足・ヒント

- テスト用のチャレンジテンプレートを `test/` などに作っておくと、問題作成者がコピペしやすい  
- `ctfcli` の詳細は [ctfcli公式ドキュメント](https://docs.ctfd.io/docs/deployment/ctfcli) を参照してください  

---

## 🤝 コントリビュート歓迎！

バグ報告・機能提案・プルリクなんでも歓迎です！
