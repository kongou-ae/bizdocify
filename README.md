# BizDocify

Morkdown からビジネス向けっぽい PDF を生成する仕組み

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


``



## カスタマイズ

## ライセンス

BizDocify は次のソフトウェアを含んでいます。

- [Vivliostyle.js](https://github.com/vivliostyle/vivliostyle.js)
