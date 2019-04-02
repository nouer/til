# Windows 10 til
## OS
### UEFIの起動方法
  - スタートメニューの電源ボタンから、Windows10の再起動をShiftを押しながら行う。
  - 青色の画面が表示されるので、トラブルシューティング→詳細オプション→UEFIファームウェアの設定を選択する

##  WSL
### Windows Subsystem for Linux のインストール
  - [Qiitaの記事](https://qiita.com/Aruneko/items/c79810b0b015bebf30bb)

### WSLの操作
  - wslの起動  
    `wsl.exe -d ubuntu`
  - wslの停止  
    `wslconfig.exe /t ubuntu`
  - 起動可能なディストリビューションのリスト表示  
    `wslconfig.exe /l`
  - ディストリビューションのアップグレード  
    `wslconfig /upgrade ubuntu`
  - パッケージのアップデート  
    `sudo apt update`
    `sudo apt upgrade`
