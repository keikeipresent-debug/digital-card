# デジタル名刺 Web サイト

YOSHITADA YAMADA の個人用デジタル名刺です。HTML・CSS・JavaScriptだけで動く静的サイトで、サーバー側のプログラムやデータベースは不要です。

## 最初に必ず行う設定

公開URLが決まったら、`config.js` の `websiteUrl` にある `YOUR_PUBLIC_URL` だけを、`https://` から始まる実際のURLに置き換えてください。通常画面のQR、QR専用画面のQR、連絡先へ保存されるURLがすべて同時に更新されます。

例：`https://example.com/digital-card/`

## 1. ローカルで確認する方法

簡単な確認なら `index.html` をダブルクリックしてブラウザで開けます。より確実に確認するには、VS Code の「Live Server」拡張機能などで `digital-card` フォルダを開いてください。

Pythonがインストールされている場合は、ターミナルで `digital-card` フォルダへ移動し、`python -m http.server 8000` を実行します。その後、ブラウザで `http://localhost:8000/` を開きます。QR専用画面は `http://localhost:8000/qr.html` です。

## 2. 氏名や肩書きを変更する方法

`config.js` の `name`、`title`、`fields`、`companyRole`、`company` を変更します。連絡先に保存する内容も変える場合は、`contact.vcf` の `N`、`FN`、`ORG`、`TITLE` も同じ内容に変更してください。

## 3. 電話番号を変更する方法

`config.js` の `phone`（表示用）と `phoneLink`（数字のみ）を変更します。さらに `contact.vcf` の `TEL` も変更してください。

## 4. メールアドレスを変更する方法

`config.js` の `email` と、`contact.vcf` の `EMAIL` を変更してください。

## 5. vCardを変更する方法

`contact.vcf` をUTF-8のままテキストエディターで編集します。各行の項目名（`FN:` や `TEL:` など）は消さず、コロンの後だけを変更してください。

## 6. 公開URLを変更する方法

`config.js` の `websiteUrl` を新しいURLに変更すると、ページ内QR、QR専用ページ、連絡先に保存されるURLがすべて更新されます。

## 7. QRコードURLを変更する方法

QRコード専用の別URLを設定したい場合も、`config.js` の `websiteUrl` を変更します。この値が両ページのQRコードに使われます。QR生成ライブラリは `assets/qrcode.js` に同梱しているため、CDNや外部サービスには依存しません。

## 8. GitHub Pagesで公開する方法

1. GitHubで新しいリポジトリを作成します。
2. `digital-card` フォルダ内のファイルをリポジトリ直下にアップロードします。
3. 「Settings」→「Pages」を開きます。
4. 「Deploy from a branch」を選び、`main` ブランチと `/ (root)` を指定して保存します。
5. 表示された公開URLを `config.js` の `websiteUrl` に設定し、変更を再度アップロードします。

## 9. Vercelで公開する方法

1. Vercelにログインし、「Add New...」→「Project」を選びます。
2. このサイトを置いたGitHubリポジトリを選びます。
3. Framework Presetは「Other」、Build Commandは空欄のままにします。
4. 「Deploy」を押します。
5. 発行されたURLを `config.js` の `websiteUrl` に設定し、GitHubへ反映します。

## 10. iPhoneでQR専用ページをホーム画面に追加する方法

1. Safariで公開済みの `qr.html` を開きます。
2. 共有ボタンを押します。
3. 「ホーム画面に追加」を選びます。
4. 名前を確認して「追加」を押します。

## 11. 公開後の確認方法

1. 通常ページと `qr.html` を開き、QRコードが表示されることを確認します。
2. 表示したQRを別のiPhoneまたはAndroidの標準カメラで読み取ります。
3. 設定した公開URLが開くことを確認します。
4. 「Add to Contacts」「Call」「Email」を実機で押し、連絡先保存・電話・メール画面が開くことを確認します。
5. QRが読みにくい場合は、画面の明るさを上げ、QR全体と白い余白が画面内に入るようにします。

## ファイル構成

```text
digital-card/
├─ index.html          通常のデジタル名刺
├─ qr.html             QR表示専用画面
├─ style.css           デザイン
├─ script.js           設定反映・QR生成
├─ config.js           プロフィールとURLの設定
├─ contact.vcf         連絡先保存用vCard
├─ README.md           この説明書
├─ .nojekyll           GitHub PagesのJekyll処理を無効化
└─ assets/
   ├─ favicon.svg      ブラウザアイコン
   └─ qrcode.js        ローカルQR生成ライブラリ（MIT License）
```
