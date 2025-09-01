# 株式会社Airu Webサイト（静的HTML版）

このフォルダには **ホーム（index.html）・会社概要（about.html）・お問い合わせ（contact.html）** と **CSS（css/styles.css）** が含まれます。  
宇宙をイメージしたグラデーション背景と星屑アニメーションを採用しています。

## 使い方

1. このフォルダをVS Codeで開く
2. `index.html` をダブルクリックしてブラウザで見た目確認
3. 会社情報（代表者・連絡先など）を `about.html` に追記
4. お問い合わせフォームはデプロイ先に応じて次の通り設定

### A. Netlify（おすすめ：フォームがそのまま動作）
- NetlifyにGit連携して本リポジトリをデプロイすると、`contact.html` のフォームが自動検出されます。
- 送信データはNetlifyの「Forms」タブで確認できます。
- 追加設定：スパム対策（honeypot）や通知メール設定はダッシュボードで可能。

### B. GitHub Pages（静的のみ）
- そのままではフォームの送信先がないため、`contact.html` の `<form>` に
  `action="https://formspree.io/f/XXXXXXXX"` を追加し、Formspreeのエンドポイントに差し替えてください。
- methodは `POST` のままでOK。

### C. Vercel（サーバレス関数で受信）
- `api/contact.js` を追加するとVercel Functionsで受け取れます（Node/Edge）。必要時に実装してください。

## デプロイ手順（超要約）

### GitHub リポジトリ作成
1. GitHubで新規リポジトリ作成（例: `airu-site`）
2. VS Codeでこのフォルダを開いてGit初期化 → コミット → 「Publish to GitHub」

### GitHub Pages
- GitHubの `Settings > Pages` で **`Deploy from a branch`** を選び、`main` / root を指定
- 公開URL: `https://<GitHubユーザー名>.github.io/<リポジトリ名>/`

### Netlify
- Netlifyにログイン → **Add new site > Import an existing project**
- GitHubリポジトリを選択。Buildは不要（静的サイト）なので `Base directory` と `Build command` は空でOK
- デプロイ後、`Forms` タブに `contact` が現れれば成功

### Vercel
- Vercelにログイン → **Add New... > Project** → GitHub連携
- Frameworkは `Other` / BuildなしでOK（静的）
- フォームをVercelで動かす場合はAPIルートを実装

---

- 事業内容の文言は、いただいた定款の「目的」の記載を要約して掲載しています。
