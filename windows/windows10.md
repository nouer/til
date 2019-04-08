# Windows 10 til
## OS
### Windowsで右Altキーに［漢字］キーを割り当てる方法
  1. レジストリエディタを起動する
  1. 以下のキーを開く  
     `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\i8042prt\Parameters`
  1. 以下のキーを編集する  

      |値の名称 |データ型 |値 |  
      |---|---|---|  
      |LayerDriver JPN|REG_SZ|kbdax2.dll|
      |OverrideKeyboardIdentifier|REG_SZ|AX_105KEY|
      |OverrideKeyboardSubtype|REG_DWORD|1|
      |OverrideKeyboardType|REG_DWORD|7|
  1. Windowsを再起動する

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

### フォルダをドライブとしてマウント
  - `subst`コマンドを利用する（管理者ではなく同一ユーザで行う）

### WSLでネットワークドライブなどのマウント
  - `mount -t drvfs [デバイス名] [マウントポイント]`
  - マウントポイントは先に作成しておく
  - デバイス名は `'`（シングルクォーテーション）で囲んでおくと無難 → `'\\shared_folder\aaa`
  - `umount [マウントポイント]`で解除

### Windowsで右Altキーに感じキーを割り当てる