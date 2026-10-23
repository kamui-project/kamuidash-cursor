# KamuiDash for Cursor

<img src="assets/logo.png" alt="KamuiDash" width="96" />

Cursorから[KamuiDash](https://dashboard.kamui-platform.com/)に接続し、アプリの状態確認、デプロイ失敗の調査、接続済みGitHubリポジトリからのデプロイを行うプラグインです。

[English](README.md)

接続先は `https://api.kamui-platform.com/mcp` です。ローカルサーバーやAPIキーの同梱はありません。

## 必要なもの

- プラグインとリモートMCPに対応したCursor。
- 操作対象のプロジェクトにアクセスできるKamuiDashアカウント。
- リポジトリからデプロイする場合は、そのリポジトリにアクセスできるKamuiDash GitHub Appの接続。

## ローカルで試す

2026-10-23 JSTにCursor Marketplaceの公開者申請を提出し、受付完了を確認しました。掲載承認は審査待ちです。Cursor内でのOAuth認証とツール実行は未検証です。現在の状況は[申請チェックリスト](docs/marketplace.md)に記載しています。

[Cursor公式のローカル検証手順](https://cursor.com/docs/plugins#test-plugins-locally)に沿って配置します。

```sh
mkdir -p ~/.cursor/plugins/local
git clone https://github.com/kamui-project/kamuidash-cursor.git ~/.cursor/plugins/local/kamuidash
```

Cursorで **Developer: Reload Window** を実行し、**Customize** からプラグインとMCPサーバーを確認します。Enterprise環境では管理者によるローカルプラグインの許可が必要な場合があります。

MCP認証を求められたら、ブラウザでKamuiDashにログインし、同意画面のアカウントと要求されたアクセスを確認して接続を許可します。サーバーはOAuthの公開情報と動的クライアント登録を提供しているため、個別のclient IDやsecretを手入力する必要はない想定です。実際のCursor環境で認証が完了することを確認してください。

### MCPだけを直接設定する場合

プラグインをインストールせずに接続を試す場合は、以下を既存のCursor MCP設定へ追加します。個人用は `~/.cursor/mcp.json`、プロジェクト用は `.cursor/mcp.json` です。既存の設定は置き換えず、項目を追加してください。接続の重複を避けるため、プラグインと直接設定のどちらか一方を使用します。

```json
{
  "mcpServers": {
    "kamuidash": {
      "url": "https://api.kamui-platform.com/mcp"
    }
  }
}
```

## 操作例

- 「KamuiDashのプロジェクト一覧と、それぞれのアプリ・デプロイ状態を教えて」
- 「このアプリの最新デプロイと実行時ログを調べて」
- 「接続済みGitHubリポジトリからNode.jsアプリをデプロイしたい。作成前に対象プロジェクト、ブランチ、リソース設定、適用料金を提示して」

GitHubからのデプロイではリモートのブランチが使われます。反映したい変更を先にpushしてください。この接続が未コミットのローカルファイルをアップロードすることはありません。

デプロイは非同期です。受付成功だけで公開完了と判断せず、デプロイ履歴とアプリの稼働状態を確認してください。

## アクセス範囲・料金・設定変更

OAuthサーバーは `full` と `offline_access` スコープを公開しています。アクセス範囲は接続したKamuiDashアカウントの権限に従い、単一プロジェクトや読み取り専用に限定されません。評価には専用のテストアカウントを使用してください。更新用のアクセスは期限切れや取り消しまで接続を維持する場合があります。

アプリ・DBの作成や容量変更では料金が発生する場合があり、アプリ更新では稼働中サービスが中断する場合があります。リソース変更前に、対象プロジェクト、ブランチ、容量、公開範囲、[最新の料金](https://dashboard.kamui-platform.com/en/documents/spec-price-overview)を確認し、意図した操作を明示的に承認してください。

秘密情報と課金設定はKamuiDashダッシュボードで管理します。パスワード、APIキー、トークン、DB接続文字列をチャットへ貼り付けないでください。既存DBをIDで関連付けると `DATABASE_URL` は自動設定されます。

## 困ったとき

- プラグインが表示されない場合は、ローカル配置先の `.cursor-plugin/plugin.json` とローカル読み込みの許可を確認し、ウィンドウを再読み込みしてください。
- 認証に失敗する場合は、CursorのMCP出力とブラウザに表示されるアカウントを確認してください。OAuth公開情報の応答だけでは認証成功を確認できません。
- リポジトリが見つからない場合は、KamuiDash GitHub Appの接続とアクセス可能なリポジトリを確認してください。
- デプロイが保留・失敗した場合は、デプロイ状態とログを確認してください。

公開Issueには認証情報や未加工のログを掲載しないでください。アカウント固有のお問い合わせは[サポートフォーム](https://dashboard.kamui-platform.com/en/inquiry)を利用してください。

## 関連リンクとライセンス

- [ダッシュボード](https://dashboard.kamui-platform.com/)
- [プライバシーポリシー](https://dashboard.kamui-platform.com/en/documents/privacy-policy)
- [利用規約](https://dashboard.kamui-platform.com/en/documents/terms-of-use)
- [申請チェックリスト](docs/marketplace.md)
- [申請文面の下書き（英語）](docs/publisher-application.md)
- [Cursorでの検証手順（英語）](docs/reviewer-walkthrough.md)

プラグインのファイルには[MITライセンス](LICENSE)を適用します。KamuiDashサービスの利用にはサービスの利用規約・料金が適用されます。このライセンスはKamuiの商標利用権を付与しません。
