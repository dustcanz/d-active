# Presence Studio

Discord Rich Presence の表示項目を編集・プレビューし、JSONとして保存する個人用Webアプリです。

## GitHub Pagesへの配置

1. GitHubで新しいリポジトリを作成します。
2. このフォルダ内の `index.html` をリポジトリ直下へ置きます。
3. リポジトリの **Settings → Pages** を開きます。
4. **Deploy from a branch** を選択し、公開するブランチ（通常は `main`）と `/ (root)` を指定して保存します。
5. 表示されたURLをスマートフォンで開きます。

## 現在の機能

- アクティビティ名、Details、Stateの編集
- 画像URLによる画像指定（画像ファイルのアップロードは行いません）
- Discord風プレビュー
- `localStorage` への自動保存
- JSONの書き出し、読み込み、クリップボードへのコピー
- 曲名・アーティスト名の手動入力とDetails / Stateへの反映

## 現時点の制約

このWebアプリは設定画面です。GitHub Pages上のブラウザJavaScriptだけでは、DiscordクライアントへRich Presenceを直接送信できません。

実際にDiscordプロフィールへ反映するには、Discord Social SDKを組み込んだネイティブアプリなど、DiscordクライアントとRPC通信する処理が必要です。AndroidではDiscord Social SDK 1.10以降に未認証RPCによるRich Presence対応があります。Discord Androidアプリがインストール済みでログインしていること、Discord Developer Portalで登録したApplication IDが必要です。

また、WebページはSpotify等の別アプリが再生している曲情報を標準機能で読み取れません。自動検出する場合は、Android側で通知アクセス権限を利用するMediaSession / NotificationListener連携などを実装する必要があります。

## データとプライバシー

設定はブラウザの `localStorage` に保存されます。このファイルは外部サーバーへ設定値を送信せず、Discordログインも要求しません。
