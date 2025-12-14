# 🍺 Beer Authenticator

**Beer CSSとMaterial Dynamic Colorsを使用した、モダンなTOTP（時間ベース ワンタイムパスワード）認証器**

QRコード読込と手入力の両方に対応し、複数のアカウントを効率よく管理できる認証アプリケーションです。

## ✨ 特徴

- 🎨 **Beer CSS + Material Dynamic Colors** - モダンで美しいUIデザイン
- 📱 **QRコード読込対応** - Google AuthenticatorやMicrosoft Authenticatorなどのサービスから簡単にアカウントをインポート
- ⌨️ **手入力対応** - Base32エンコードされたシークレットキーを直接入力可能
- 👥 **複数アカウント管理** - 無制限にアカウントを登録・管理
- 🔒 **ローカルストレージ保存** - シークレットキーはブラウザのローカルストレージに安全に保存（外部サーバーに送信しない）
- 🌓 **ダーク/ライトモード対応** - システム設定に応じて自動切替
- ⏱️ **リアルタイムカウントダウン** - 残り時間を進捗バーで表示
- 📋 **ワンクリックコピー** - 生成されたコードをクリップボードに即座にコピー
- 📱 **レスポンシブデザイン** - スマートフォン・タブレット・PCで快適に使用可能

## 🚀 使い方

### 1. アプリケーションを開く

```
https://yunfie-twitter.github.io/beer-authenticator/
```

### 2. アカウントを追加

#### QRコードから読込（推奨）
1. 左のパネルで「QRコード」タブを選択
2. ファイルをアップロードするか、カメラで撮影
3. 「QRコードを読み込む」をクリック
4. Google AuthenticatorやMicrosoft Authenticatorから表示されるQRコードをスキャン

#### 手入力
1. 左のパネルで「手入力」タブを選択
2. アカウント名を入力（例：GitHub、Gmail）
3. 発行者を入力（オプション、例：github.com）
4. Base32エンコードされたシークレットキーを入力
5. 「アカウントを追加」をクリック

### 3. コードを使用

- 右パネルに登録済みアカウントと現在のTOTPコードが表示されます
- コードは30秒ごとに更新されます
- 「コピー」ボタンをクリックしてコードをクリップボードにコピーできます
- 「削除」ボタンでアカウントを削除できます

## 🔐 セキュリティ

- ✅ **クライアントサイドのみ処理** - すべての処理がブラウザで完結し、サーバーに情報は送信されません
- ✅ **ローカルストレージ保存** - シークレットキーはブラウザのlocalStorageに保存されます
- ✅ **オープンソース** - コードは完全に透明で、誰でも検査可能です

**注意：** ブラウザのlocalStorageはデバイスのローカルストレージです。デバイスが盗まれたり、侵害されたりした場合、アカウントが危険にさらされる可能性があります。定期的なバックアップと、複数のデバイスでの認証器の設定をお勧めします。

## 📦 依存ライブラリ

- **[Beer CSS](https://www.beercss.com/)** v3.13.1 - UI フレームワーク
- **[Material Dynamic Colors](https://material.io/blog/dynamic-color)** v1.1.2 - ダイナミックカラーシステム
- **[jsQR](https://github.com/cozmo/jsQR)** v1.4.0 - QRコード読込
- **[OTPAuth](https://github.com/hectorm/otpauth)** v9.2.2 - TOTP/HOTP実装

## 💾 データ管理

すべてのアカウント情報はブラウザのlocalStorageに保存されます：

```javascript
{
  "id": 1702516440000,
  "name": "GitHub",
  "issuer": "github.com",
  "secret": "JBSWY3DPEBLW64TMMQQ",
  "createdAt": "2024-12-14T06:14:00.000Z"
}
```

### データをエクスポート

ブラウザのコンソール（F12キー）で以下を実行：

```javascript
console.log(JSON.stringify(JSON.parse(localStorage.getItem('beer-authenticator-accounts')), null, 2));
```

### データをインポート

ブラウザのコンソール（F12キー）で以下を実行：

```javascript
localStorage.setItem('beer-authenticator-accounts', JSON.stringify([/* ここに配列を貼付 */]));
location.reload();
```

## 🛠️ 開発

### ローカルで実行

```bash
# シンプルHTTPサーバーで実行
python -m http.server 8000
# または
npx http-server

# ブラウザで開く
open http://localhost:8000
```

### ビルド・デプロイ

このプロジェクトはスタティックHTMLのみなため、ビルドプロセスは不要です。

GitHub Pagesで自動的にデプロイされます：

```
https://yunfie-twitter.github.io/beer-authenticator/
```

## 📱 ブラウザサポート

- ✅ Chrome/Chromium 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## 📄 ライセンス

MIT License - 詳細は [LICENSE](./LICENSE) をご覧ください

## 🤝 貢献

バグ報告、機能提案、プルリクエストを歓迎します！

## ⚠️ 免責事項

このアプリケーションはコミュニティによる無償提供です。本アプリケーションの使用により生じたあらゆる損害について、開発者は一切の責任を負いません。

## 🔗 関連リンク

- [RFC 6238 - TOTP](https://tools.ietf.org/html/rfc6238)
- [RFC 4648 - Base32 Encoding](https://tools.ietf.org/html/rfc4648)
- [Key Uri Format](https://github.com/google/google-authenticator/wiki/Key-Uri-Format)

---

🍺 Made with ❤️ using Beer CSS
