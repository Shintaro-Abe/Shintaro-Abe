# Tips
## リポジトリファイルのダウンロードURL
- パーマリンクの一部を変更。
    - `https://github.com/RepositoryName/blob/.......`の` blob `を`raw `へ修正。 
```
https://github.com/Shintaro-Abe/Shintaro-Abe/blob/5457699c248d540fdf9ab7490c8413522edb8ffb/docs/README.pdf
```
の場合、
```
https://github.com/Shintaro-Abe/Shintaro-Abe/raw/5457699c248d540fdf9ab7490c8413522edb8ffb/docs/README.pdf
```
にする。

## GitHub PagesのPDFからリンク差し替え
ルートディレクトリにあるgitpdf.shで自動化。
以下のコマンドを使用。
```
bash gitpdf.sh
```
詳細は、[GitHub-Pages-PDF](https://github.com/Shintaro-Abe/GitHub-Pages-PDF)リポジトリを参照。