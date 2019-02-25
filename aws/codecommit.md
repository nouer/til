# CodeCommit

## トラブル集
  - Permission denied (publickey) が表示される  
    sshのユーザ名か、pemが間違っていることが多い  
    IAMから、確認する  
    ユーザ名は、IAMのAWS CodeCommitのSSHキー項目の中にある、SSHキーIDを設定する。アクセスキーIDを指定してハマること多数。  
    秘密鍵、公開鍵が間違っていることもあるので、再度登録し直すとうまくいくことが多い。
