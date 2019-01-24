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
# アーキテクチャ

---
class: center, middle

![architecture](https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Kubernetes.png/660px-Kubernetes.png)

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
## etcd

- 永続的で軽量な分散Key-Valueストア
- クラスタの設定や状態を保存

---
## API Server

- Kubernetes APIのサーバー
- Kubernetesに対する内外のインターフェースを提供する

---
## Scheduler

- 新規Podを最適なノードに配置
- リソースの供給を需要に合わせる

---
## Controller Manager

- クラスタの状態を維持
    - レプリカ数
    - ジョブ

---
## Kubelet

- ノード内の管理
    - Podの状態を監視、異常があれば再デプロイ
    - ノード状態をマスターに送信

---
## Kube-proxy

- プロキシ、ロードバランサーの役割

---
## cAdvisor

- リソースの使用量を監視、収集

---
class: center, middle, inverse
# リソース

---
## リソース

- ReplicaSet
- Deployment
- DaemonSet
- Job
- CronJob
- Service
- Ingress
- Namespace

---
## リソース

- Secret
- StatefulSet
- Volume
- PersistentVolume

---
## ReplicaSet

- Podを管理、複製
    - セルフヒーリング

---
## Deployment

- ReplicaSetの履歴管理
    - 更新、ロールバック、削除

---
## DaemonSet

- 各ノードに1つずつPodを配置する

---
## Job

- 1度のみ実行する

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
## Secret

- 機密情報を定義
    - kubesec

---
## ConfigMap

- Key-Valueでデータを保持

---
## StatefulSet

- データの永続化

---
## Volume

- ホスト上の領域をマッピング

---
## PersistentVolume

- 永続化領域

---
class: center, middle, inverse
# マニフェスト例

---
## Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: sample-pod
spec:
  containers:
    - name: nginx-container
      image: nginx:1.12
```

---
## ReplicaSet

.zoom1[
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: sample-rs
spec:
  replicas: 3
  selector:
    matchLabels:
      app: sample-app
  template:
    metadata:
      labels:
        app: sample-app
    spec:
      containers:
        - name: nginx-container
          image: nginx:1.12
          ports:
            - containerPort: 80

```
]

---
## Deployment

.zoom1[
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sample-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: sample-app
  template:
    metadata:
      labels:
        app: sample-app
    spec:
      containers:
        - name: nginx-container
          image: nginx:1.12
          ports:
            - containerPort: 80
```
]

---
## Job

.zoom1[
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: sample-job
spec:
  completions: 1
  parallelism: 1
  backoffLimit: 10
  template:
    spec:
      containers:
      - name: sleep-container
        image: centos:6
        command: ["sleep"]
        args: ["60"]
      restartPolicy: Never
```
]

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

---
## 参考サイト

<https://kubernetes.io/docs/home/>

<https://www.cncf.io/phippy/>

<https://github.com/kubernetes>