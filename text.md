# WSLの環境構築
[参考URL](https://docs.microsoft.com/ja-jp/windows/wsl/install)  
今回の方法はwindows10 build 2004以降、windows11で有効  
windows10のビルド番号は、「設定、バージョン情報、OSビルド」で確認。  
## WSLのインストール
powershellを管理権限で開き、下記のコマンドを実行する。  
(powershellはスタートボタンから検索。複数の方法あり)
```powershell
wsl --install
```  
＊必ずwindowsの更新プログラムがすべて実行されてから、インストールを行うこと。新しいパソコンは特に注意。
## WSLの起動
windowsターミナル（おすすめ）、またはPowerShellを起動する。必要ないかも？    
(windows10の場合はダウンロード:[url](https://docs.microsoft.com/ja-jp/windows/terminal/))
```powershell
wsl
```
と入力するとwslが起動する。  
ユーザ名、パスワードを設定すると、Linuxのターミナルが起動する。
## WSLの初期設定
### リポジトリの変更
デフォルトではUSのリポジトリになっており、速度が遅いため国内のミラーリポジトリへ変更する。  
```bash
sudo sed -i.org -e 's|archive.ubuntu.com|ftp.jaist.ac.jp/pub/Linux/ubuntu|g' /etc/apt/sources.list
```
パッケージを更新する。  
```bash
sudo apt update && sudo apt upgrade -y
```
＊このコマンドは、定期的に実行すること。
これで`sudo apt install hogehoge`で好きなパッケージをインストールできるようになった。  
## Windows Terminalの設定
色々設定できるが、開始ディレクトリをwindowsのユーザーホーム（C:\Users\USERNAME）にすると便利。  

## Xserverの導入
windows11ではwslgが使えるが、ここではVcXsrvを用いて環境構築を行う。

## 今までで発生したトラブル事例
- 0x800720efd→更新プログラムが実行中
- 0x800701bc→カーネルをアップデートする（[ダウンロード先](https://docs.microsoft.com/ja-jp/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)）