# 04 pfSense インストール  

**English version →** [04-pfsense-installation.md](../docs/04-pfsense-installation.md)


VirtualBox におけるファイアウォール／ルーターの構築

pfSense は本ラボの VirtualBox 環境におけるファイアウォール兼ルーターとして動作します。このドキュメントでは、pfSense のインストール、インターフェース設定、初期セットアップ手順を説明します。

---

## pfSense ISO のダウンロード

以下から pfSense Community Edition の最新 ISO をダウンロードします。

https://www.pfsense.org/download/

推奨設定：

- アーキテクチャ：**AMD64**
- インストーラ：**ISO**
- コンソール：**VGA**
- ミラー：最寄りの地域

ダウンロード後、pfSense VM の仮想光学ドライブにマウントします。

---

## インストーラの起動

1. pfSense VM を起動  
2. **Install pfSense** を選択  
3. キーマップはデフォルトで OK  
4. ディスクレイアウトは **Auto (ZFS)** または **UFS**（どちらでも可）  
5. インストール完了後、再起動  

---

## 初期コンソール設定

再起動後、pfSense は 2 つのインターフェースを検出します。

- **WAN**（NAT アダプタ）  
- **LAN**（Host-Only アダプタ）  

デフォルト設定：

- WAN：DHCP（VirtualBox NAT から取得）  
- LAN：`192.168.1.1/24`  

ラボの一貫性のため、LAN を以下に変更することを推奨します。

- LAN IP：`10.0.0.1/24`

変更手順：

1. コンソールで **2) Set interface IP address** を選択  
2. **LAN** を選択  
3. IP：`10.0.0.1`  
4. サブネット：`24`  
5. ゲートウェイ：なし  
6. DHCP サーバー：任意  
7. HTTPS を維持  

---

## WebGUI へのアクセス

RHEL サーバーまたはホスト PC から以下にアクセスします。
```markdown
https://10.0.0.1 (10.0.0.1 in Bing)
```

初期ログイン情報：

- ユーザー名：`admin`  
- パスワード：`pfsense`  

初回ログイン後、セットアップウィザードが開始されます。

---

## セットアップウィザード

推奨設定：

- ホスト名：`pfsense`  
- ドメイン：`local.lan`  
- DNS：任意（空欄でも可）  
- WAN：DHCP  
- LAN：`10.0.0.1/24`  
- 管理者パスワード：任意の安全な値  

---

## 接続確認

pfSense コンソールから：
```markdown
ping 8.8.8.8
```


RHEL サーバーから：
```markdown
ping 10.0.0.1
```


期待される結果：

- pfSense → インターネット到達  
- RHEL → pfSense LAN 到達  

---

## スクリーンショット

以下のスクリーンショットは `07-スクリーンショット.md` に掲載しています。

- インストーラ画面  
- インターフェース割り当て  
- セットアップウィザード  
- ダッシュボード  

---


