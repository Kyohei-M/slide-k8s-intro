name: inverse
layout: true
class: center, middle, inverse

---
# Kubernetes入門

---
layout: false
## 対象者

- Kubernetes未経験者

---
class: center, middle, inverse
# Kubernetesとは

---
## Kubernetes？

- コンテナオーケストレーションツール
- オープンソース

![kubernetes](https://upload.wikimedia.org/wikipedia/en/0/00/Kubernetes_%28container_engine%29.png)

---
## コンテナ？

- プロセスを1つの環境として切り分けたもの
- 軽量かつ移植、複製が容易

---
## オーケストレーション？

- 配置、設定、管理の自動化

---
## Kubernetesの利用

- オンプレミス
    - Minikube
    - Open Stack
    - Rancher
- マネージドサービス
    - GKE
    - AKS
    - EKS
    - OpenShift

---
class: center, middle, inverse
# 機能

---
## 機能

- 仕様、設定管理
- リソース作成、配置
- リソース拡張
- 通信
- ジョブ管理
- ログ管理
- 冗長性
- 認証・認可

---
## 仕様、設定管理

- コードベースの仕様
    - マニフェスト
    - Infrastructure as Code

---
## リソース作成、配置

- 設定に従って必要なリソースを作成、配置
- バージョン管理
    - ローリングアップデート
    - ロールバック

---
## リソース拡張

- リソースの不足時に自動拡張
    - オートスケーリング

---
## 通信

- 外部との通信
- 内部の通信
    - オーバーレイネットワーク
    - 内部DNS

---
## ジョブ管理

- スケジューリング

---
## ログ管理

- 各リソースのログを集約
- 外部ツールと連携

---
## 冗長性

- 死活監視
    - セルフヒーリング
- ロードバランシング

---
## 認証・認可

- アカウント管理
- 権限の分離
    - RBAC

---
class: center, middle, inverse
# リソース

---
## リソース

- Cluster
- Master
- Node
- Pod
- ReplicaSet
- Deployment
- Job
- CronJob

---
## リソース

- Service
- Ingress
- Namespace
- Volume

---
## Cluster

- Kubernetes実行環境の基盤

---
## Master

- クラスタ全体の管理ユニット

---
## Node

- コンテナが動作する環境
- マシンリソース

---
## Pod

- 1つ以上のコンテナを内包する単位

---
## ReplicaSet

- Podを管理、複製
    - セルフヒーリング

---
## Deployment

- ReplicaSetの履歴管理
    - 更新、ロールバック、削除

---
## Job

- 1度のみ実行するプロセス

---
## CronJob

- Jobのスケジューリング

---
## Service

- コンテナと外部の通信
    - L4ロードバランシング
---
## Ingress

- クラスタと外部の通信
    - L7ロードバランシング

---
## Namespace

- リソースの分割
- 仮想クラスタ

---
## Volume

- ストレージの共有

---
class: center, middle, inverse
# 書籍紹介

---
class: center, middle
<img src="https://images-na.ssl-images-amazon.com/images/I/81nkS-qu9gL.jpg" width=55%>

---
class: center, middle
<img src="http://image.gihyo.co.jp/assets/images/cover/2018/9784297100339.jpg" width=55%>

---
class: center, middle
<img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=55%>

---
class: center, middle
<img src="https://images-na.ssl-images-amazon.com/images/I/71F%2BqeYXNgL.jpg" width=55%>