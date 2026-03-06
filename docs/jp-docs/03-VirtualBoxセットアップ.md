# 03 VirtualBox セットアップ 

**English version →** [03-virtualbox-setup.md](../docs/03-virtualbox-setup.md)


仮想化環境の準備

このセクションでは、VirtualBox のインストール、ホスト側の設定、そして本ラボで使用する仮想マシン（pfSense と RHEL サーバー）の作成手順について説明します。VirtualBox 環境は、企業ネットワークの境界（ファイアウォール）とサーバーレイヤーを再現する基盤となります。

---

## VirtualBox のインストール

VirtualBox は Windows / macOS / Linux で利用できます。以下から最新バージョンをダウンロードします。

https://www.virtualbox.org/wiki/Downloads

次の 2 つをインストールしてください。

- VirtualBox 本体  
- VirtualBox Extension Pack（推奨）

インストール後、VirtualBox を起動して仮想マシンの作成を開始します。

---

## pfSense VM の作成

### 推奨設定

| 設定項目 | 値 |
|---------|-----|
| 名前 | pfSense |
| OS タイプ | BSD |
| バージョン | FreeBSD (64-bit) |
| CPU | 2 |
| RAM | 2 GB |
| ディスク | 10 GB |
| ネットワークアダプタ 1 | NAT（WAN） |
| ネットワークアダプタ 2 | Host-Only（LAN） |

### 手順

1. **新規** → 名前を `pfSense` に設定  
2. OS を **BSD → FreeBSD (64-bit)** に設定  
3. **2 GB RAM** と **2 CPU** を割り当て  
4. **10 GB の VDI ディスク** を作成  
5. **設定 → ネットワーク**  
   - アダプタ 1：NAT  
   - アダプタ 2：Host-Only  
6. **ストレージ** で pfSense ISO をマウント  

スクリーンショットは `07-スクリーンショット.md` に掲載しています。
