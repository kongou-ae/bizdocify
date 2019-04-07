# BizDocify

Morkdown からビジネス向けっぽい PDF を生成する仕組み

## 出来上がりのサンプル

[input](https://github.com/kongou-ae/bizdocify/tree/master/sample/content) --> [output.pdf](https://github.com/kongou-ae/bizdocify/raw/master/sample/output.pdf)

## インストール方法（Windows向け）

```powershell
$ErrorActionPreference = "stop"
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12

$bizdocifyUrl = "https://github.com/kongou-ae/bizdocify/archive/master.zip"
$hugoUrl = "https://github.com/gohugoio/hugo/releases/download/v0.54.0/hugo_extended_0.54.0_Windows-64bit.zip"

Invoke-WebRequest -Uri $bizdocifyUrl -OutFile $HOME/Downloads/bizdocify.zip
Expand-Archive -Path $HOME/Downloads/bizdocify.zip -DestinationPath $HOME

Invoke-WebRequest -Uri $hugoUrl -OutFile $HOME/Downloads/hugo.zip
Expand-Archive -Path $HOME/Downloads/hugo.zip -DestinationPath $HOME
mv $HOME\hugo.exe $HOME\bizdocify-master
```

## 使い方

### ドキュメントの書き方

- `config.toml` にドキュメントの基本情報を記載します
- `.\hugo.exe new content\YOURFILENAME.md` で空ファイルを作成します
- `title:` と `Author:` を記入します
    - 複数の Markdown ファイルが存在する場合、Markdown ファイルを `title:` に記載された文字列の順番で整列したうえで PDF ファイルを生成します
- 好きな文章を Markdown ファイルに書きます

### 出来上がりの確認方法

- `.\hugo.exe server` を実行して、Web Server を起動します
- `tools.html` を開いて `Viewer` をクリックします
- 表示された Vivliostyle Viewer を利用して、できあがりの PDF の見た目を確認します
    - Markdown を更新した場合、Vivliostyle Viewer を手動でリロードしてください
    - 更新が反映されない場合、DevTool を 利用して Chrome のキャッシュを無効化してください

### PDF の出力方法

Google Chrome で Vivliostyle Viewe にアクセスしたうえで、右クリック → 印刷 を選択して PDF として保存します。

## ショートコード

Markdown にショートコードを追記することで、PDF ファイルに情報を追加できます。

### img

画像の記法を次のように囲うと、画像に図表番号が付与されます。

```
{{% img title="App Service の全体図" %}}
![aaaaa](/images/2019-03-05-001.PNG)
{{% /img %}}
```

### table

テーブルの記法を次のように囲うと、テーブルに図表番号が付与されます。

```
{{% table  title="利用するFQDN一覧" %}}
| No | 管理者 | 利用者 |
|------------|------------|----------------|
| 1 |adminportal.region.fqdn|portal.region.fqdn|
|2 |adminmanagement.region.fqdn|management.region.fqdn|
{{% /table %}}
```

## ライセンス

- GNU Affero General Public License v3.0
- BizDocify は次のソフトウェアを含んでいます。
    - [Vivliostyle.js](https://github.com/vivliostyle/vivliostyle.js)
