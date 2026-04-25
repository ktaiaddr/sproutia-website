# sproutia-website

Sproutia のコーポレートサイト（`https://sproutia.jp/`）。

現時点では、Google Play ストア公開および Google OAuth 同意画面に必要な
**プライバシーポリシー** の公開が主目的。

## ディレクトリ構成

```
sproutia-website/
├── CNAME               # GitHub Pages の独自ドメイン設定 (sproutia.jp)
├── index.html          # トップページ
├── privacy/
│   └── index.html      # プライバシーポリシー (https://sproutia.jp/privacy/)
└── README.md
```

各 HTML ファイルを直接編集する運用。将来ページが増えて管理が辛くなってきたら
Jekyll（GitHub Pages 標準対応）でのビルド化を検討する。

## 公開手順（初回）

### 1. GitHub リポジトリ作成

GitHub 上で `sproutia-website` という Public リポジトリを作成する。

### 2. ローカルから push

```bash
cd ~/AndroidStudioProjects/sproutia-website
git init
git add -A
git commit -m "Initial commit: privacy policy and landing page"
git branch -M main
git remote add origin git@github.com:<your-username>/sproutia-website.git
git push -u origin main
```

### 3. GitHub Pages を有効化

1. リポジトリの `Settings` → `Pages`
2. `Source` を `Deploy from a branch` に設定
3. `Branch` を `main` / `/ (root)` に設定して保存

数分後、`https://<your-username>.github.io/sproutia-website/` で閲覧できる。

### 4. 独自ドメイン (sproutia.jp) を設定

1. `Settings` → `Pages` → `Custom domain` に `sproutia.jp` を入力して保存
   （既にリポジトリに `CNAME` ファイルがあるので自動的に埋まる場合あり）
2. お名前.com の DNS 設定で、以下を登録する：

   **A レコード（Apex ドメイン `sproutia.jp` 用）**
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   **CNAME レコード（`www.sproutia.jp` 用・任意）**
   ```
   www   →   <your-username>.github.io
   ```

3. DNS 伝播（最大 24 時間、通常 1 時間以内）を待ち、`Settings` → `Pages` で
   `Enforce HTTPS` にチェックを入れる

### 5. 動作確認

- `https://sproutia.jp/` → トップページ表示
- `https://sproutia.jp/privacy/` → プライバシーポリシー表示

## 更新手順

1. `privacy/index.html` を直接編集
2. 文中の `最終更新日` を更新
3. コミット → push

変更は `main` にマージされて数十秒〜数分で自動反映される。

## 関連

- Google Play 開発者アカウント登録時に `https://sproutia.jp/privacy/` を URL として登録
- OAuth 同意画面の本番化時にも同じ URL を使う
