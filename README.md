# ILLUST DRAFT BATTLE - BO3 / 3TYPE

GitHub Pages とローカルHTMLの両方で動かせる構成です。

## 画像モード

### 標準イラスト
`assets/images/default/` の画像を使います。
このフォルダの画像一覧は `assets/default-images.js` に記録します。

### 自分の画像フォルダ
ゲーム画面の「自分の画像フォルダ」から、PC上の好きな画像フォルダを選べます。
現在想定しているローカルフォルダは `D:\PixAI\Card` です。
選択したフォルダはブラウザ側に保存され、対応ブラウザでは次回以降も復元を試みます。

## D:\PixAI\Card の画像をGitHub用にコピー

Windows PowerShellで、リポジトリの `tools\import-card-images.ps1` を一度実行してください。

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\import-card-images.ps1
```

これで、

- `D:\PixAI\Card` の画像を `assets/images/default/` にコピー
- `assets/default-images.js` を自動更新

します。

## GitHub Pages

リポジトリのルートに `index.html` があるので、そのままPages公開できます。
GitHub側で Settings → Pages から、公開元をリポジトリのブランチ/ルートに設定してください。

## ローカル版

`index.html` をブラウザで開いて遊べます。
標準画像はリポジトリ内の相対パスを使うため、GitHub Pagesとローカルの両方で同じ構成になります。

## 注意

`assets/images/custom/` は、個人用画像をリポジトリへ入れたい場合の置き場所です。公開したくない画像はGitHubへコミットせず、ゲーム画面からローカルフォルダを選択してください。

## PNG → WEBP 変換

カード画像を軽量化したい場合は、`tools/convert-png-to-webp.bat` をダブルクリックしてください。

- 対象: `D:\PixAI\Card` の PNG
- 出力: 同じフォルダに同名の `.webp`
- 変換後、元PNGを残すか削除するか選べます
- ImageMagick → FFmpeg → Python + Pillow の順で利用できる環境を自動判定します

Python + Pillow を使う場合は、事前に次を実行します。

`py -m pip install Pillow`
