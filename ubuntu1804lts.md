# Ubuntu 18.04 LTS メモ
## SSH接続設定
### インストール
```sh
sudo apt-get install aptitude
sudo aptitude install ssh
```
### 設定
```sh
sudo vi /etc/ssh/sshd_config
```

### 公開鍵認証設定
####  公開鍵、秘密鍵の設定
```sh
ssh-keygen -t rsa
```
- 以下に作成される。
```sh
#公開鍵
~/ssh/id_rsa.pub
#秘密鍵
~/.ssh/id_rsa
```
- Macの場合、キーチェーンに登録
```sh
ssh-add -K ~/.ssh/id_rsa
```
#### 公開鍵をサーバーに登録
- 対象サーバーの ~/.ssh/authorized_keys へ登録。
##### 手動で登録する
- 必要なフォルダとファイルを作成
```sh
ssh hogehoge@hogehoge.com
mkdir .ssh
touch .ssh/authorized_keys
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
```
- 対象サーバーのauthorized_keysに追記
cat ~/.ssh/id_rsa.pub | ssh hogehoge@hogehoge.com 'cat >> .ssh/authorized_keys'

#### 確認
#### パスワード認証の禁止設定
