# 08 再現手順  
ラボ環境をゼロから再構築するための手順

このドキュメントでは、本プロジェクトで使用した VirtualBox および Packet Tracer の環境を、最初から再現するための完全な手順をまとめています。ここに記載された手順に従うことで、誰でも同じラボ環境を構築できます。

---

## 必要要件

### ソフトウェア
- VirtualBox（最新バージョン）
- VirtualBox Extension Pack（推奨）
- pfSense CE ISO
- RHEL ISO
- Cisco Packet Tracer（最新バージョン）

### ハードウェア
- 最低 8 GB RAM（推奨 16 GB）
- 40〜60 GB の空きディスク容量
- 仮想化支援機能（Intel VT-x / AMD-V）対応 CPU

---

## Part 1 — VirtualBox 環境の構築

### Step 1: VirtualBox のインストール
公式サイトから VirtualBox をダウンロードしてインストールします。

### Step 2: Host-Only ネットワークの作成
1. **ツール → ネットワークマネージャー** を開く  
2. Host-Only ネットワークを作成または確認  
   - IP：`10.0.0.1`  
   - マスク：`255.255.255.0`  
   - DHCP：無効  

### Step 3: pfSense VM の作成
1. 新規 VM → 名前：`pfSense`  
2. OS：BSD → FreeBSD (64-bit)  
3. CPU：2  
4. RAM：2 GB  
5. ディスク：10 GB  
6. ネットワーク：  
   - アダプタ 1：NAT  
   - アダプタ 2：Host-Only  
7. pfSense ISO をマウント  

### Step 4: pfSense のインストール
1. VM を起動  
2. **Install pfSense** を選択  
3. デフォルト設定で進める  
4. 再起動  
5. インターフェース割り当て  
6. LAN IP を `10.0.0.1/24` に設定  

### Step 5: RHEL サーバー VM の作成
1. 新規 VM → 名前：`server01`  
2. OS：Linux → Red Hat (64-bit)  
3. CPU：2  
4. RAM：2〜4 GB  
5. ディスク：20 GB  
6. ネットワーク：Host-Only  
7. RHEL ISO をマウント  

### Step 6: RHEL のインストール
1. インストーラを起動  
2. 通常の手順で OS をインストール  
3. 必要に応じて静的 IP を設定  
   - IP：`10.0.0.x`  
   - ゲートウェイ：`10.0.0.1`  

### Step 7: 接続確認
RHEL から：
```markdown
ping 10.0.0.1
```

期待される結果：pfSense LAN に到達できる。

---

## Part 2 — Packet Tracer 環境の構築

### Step 1: トポロジーの作成
1. ルーターを 1 台追加  
2. スイッチを 1〜2 台追加  
3. PC を 2 台以上追加  

### Step 2: ルーターの設定
例：
```markdown
interface g0/0 ip address 192.168.1.1 255.255.255.0 no shutdown
```


### Step 3: スイッチの設定
例：

```markdown
interface range f0/1 - 24 switchport mode access switchport access vlan 1
```

### Step 4: PC の設定
例：

- IP：`192.168.1.10`  
- マスク：`255.255.255.0`  
- ゲートウェイ：`192.168.1.1`  

### Step 5: 接続確認
```markdown
ping 192.168.1.1 ping 192.168.1.11
```

期待される結果：  
- ルーターに到達可能  
- 同一 VLAN 内のホスト同士が通信可能  

---

## Part 3 — 概念的な統合

VirtualBox と Packet Tracer は技術的には接続されていませんが、以下のように役割が対応しています。

- VirtualBox → 境界ファイアウォール + サーバーレイヤー  
- Packet Tracer → 内部 LAN（ルーティング／スイッチング）  

これにより、企業ネットワークの全体像を理解しながら、各レイヤーの役割を学習できます。

---

## トラブルシューティング

### pfSense LAN に接続できない
- Host-Only アダプタが有効か確認  
- LAN IP が正しいか確認  
- RHEL の NIC 設定を確認  

### Packet Tracer のホスト間で通信できない
- ルーターのインターフェースが up か確認  
- PC のゲートウェイ設定を確認  
- スイッチポートが有効か確認  

---

## 完了

この手順を完了すると、以下が再現できます。

- VirtualBox 上の pfSense + RHEL サーバー環境  
- Packet Tracer 上の Cisco LAN トポロジー  
- 企業ネットワークを模した概念的な統合モデル  
- 英日バイリンガルの再現性の高いドキュメントセット  

これで Virtualization & Network Simulation Lab の再現手順は完了です。

