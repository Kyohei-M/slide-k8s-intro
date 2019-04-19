name: inverse
layout: true
class: center, middle, inverse

---
# Kubernetes入門

---
layout: false
### whoami

.left-small[
    ![image](https://pbs.twimg.com/profile_images/994762110792953856/EheEvqBY_400x400.jpg)
]

.right-large[
- Kyohei Mizumoto(@kyohmizu)

- C# Software Engineer

- Interests
    - Docker/Kubernetes
    - Go
    - Security
]

---
### 対象者

- Kubernetesやったことない、知らない

- Kubernetesに興味がある

- Kubernetesの概要を知りたい

---
### 目次

- Kubernetesとは

- Kubernetesの機能

- アーキテクチャ

- Kubernetesリソース

- マニフェスト例

---
class: center, middle, inverse
# Kubernetesとは

---
### Kubernetes？

.left-large[
- コンテナオーケストレーションツール

- オープンソース

- Cloud Native Computing Foundation (CNCF)がホスト
]

.right-small[ ![kubernetes](https://upload.wikimedia.org/wikipedia/en/0/00/Kubernetes_%28container_engine%29.png) ]

---
### コンテナ？

- 仮想化技術の一種

- プロセスを1つの環境として切り分けたもの

- 軽量かつ移植、複製が容易

- Dockerがデファクトスタンダード

---
### オーケストレーション？

.zoom2[
- 配置、設定、管理の自動化

  - Webアプリ

  - 内部プログラム

  - データベース

  - ネットワーク

- Kubernetesは全てをリソースとして管理
]

---
### Kubernetesの利用

.zoom2[
- ローカル

  - Minikube

  - Docker for Mac

- Kubernetes構築ツール

  - kubeadm

  - Rancher
]

---
### Kubernetesの利用

- マネージドサービス

  - Google Kubernetes Engine（GKE）

  - Azure Container Service（AKS）

  - Elastic Container Service for Kubernetes（EKS）

---
class: center, middle, inverse
# Kubernetesの機能

---
### Kubernetesの機能

.zoom0[
- 仕様、設定管理

- リソース作成、配置

- リソース拡張

- 通信

- ジョブ管理

- ログ管理

- 冗長性

- 認証・認可
]

---
### 仕様・設定管理

- コードベースの仕様

    - yaml形式のマニフェストファイル

    - Infrastructure as Code

---
### リソース作成・配置

- 設定に従って必要なリソースを作成、配置

- バージョン管理

    - ローリングアップデート

    - ロールバック

---
### リソース拡張

- リソースの不足時に自動拡張

    - オートスケーリング

---
### 通信

- 外部との通信

  - プロキシ

- 内部の通信

    - オーバーレイネットワーク

    - 内部DNS

---
### ジョブ管理

- スケジューリング

  - 1回のみ
  
  - 繰り返し

---
### ログ管理

- 各リソースのログを集約

- 外部ツールと連携

  - 監視

  - アラート

---
### 冗長性

- 死活監視

    - セルフヒーリング

- ロードバランシング

---
### 認証・認可

- アカウント管理

- 権限の分離

    - RBAC

---
class: center, middle, inverse
# アーキテクチャ

---

<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Kubernetes.png/660px-Kubernetes.png" width=100%></center>

---
### Cluster(クラスタ)

- Kubernetes実行環境の基盤

  - 1つ(以上)のmaster

  - 複数のnode

---
### Master(マスター)

- クラスタ全体の管理ユニット

  - etcd

  - API Server

  - Scheduler

  - Controller Manager

---
### Node(ノード)

- コンテナが動作する環境、マシンリソース

  - Pod

  - Kubelet

  - Kube-proxy

  - cAdvisor

---
### etcd

- 永続的で軽量な分散Key-Valueストア

- クラスタの設定や状態を保存

---
### API Server

- Kubernetes APIのサーバー

- Kubernetesに対する内外のインターフェースを提供する

---
### Scheduler

- 新規Podを最適なノードに配置

- リソースの供給を需要に合わせる

---
### Controller Manager

- クラスタの状態を維持

    - レプリカ数

    - ジョブ管理

---
### Pod

- 1つ以上のコンテナを内包する単位

- Pod内はlocalhostでアクセス可能

---
### Kubelet

- ノード内の管理

    - Podの状態を監視、異常があれば再デプロイ

    - ノード状態をマスターに送信

---
### Kube-proxy

- プロキシ、ロードバランサーの役割

### cAdvisor

- リソースの使用量を監視、収集

---
class: center, middle, inverse
# Kubernetesリソース

---
### リソースの分類

- Workloadsリソース

- Discovery＆LBリソース

- Config＆Storageリソース

- Clusterリソース

- Metadataリソース

---
class: center, middle, blue
## Workloadsリソース

---
### Workloadsリソース

.zoom2[
- Pod

- ReplicaSet

- Deployment

- DaemonSet

- StatefulSet

- Job

- CronJob
]

---
### ReplicaSet

- Podの管理、複製

  - Pod数を設定どおりに維持

  - セルフヒーリング

---
### Deployment

- ReplicaSetの履歴、バージョン管理

  - アップデート
    
  - ロールバック
  
  - 削除

---
### DaemonSet

- 各ノードに1つずつPodを配置

  - e.g. ノードの管理、情報収集

---
### Job

- 1度のみ実行

### CronJob

- Jobのスケジューリング

---
class: center, middle, blue
## Discovery＆LBリソース

---
### Discovery＆LBリソース

.zoom1[
- Service

  - ClusterIP

  - NodePort

  - LoadBalancer

  - ExternalIP

  - ExternalName

  - Headless

- Ingress
]

---
### Service

- コンテナと外部の通信

  - クラスタ内

  - クラスタと外部

  - IPアドレス、ポートによるアクセス
---
### Ingress

- クラスタと外部の通信

  - URLによるアクセス

  - L7ロードバランシング

---
class: center, middle, blue
## Config＆Storageリソース

---
### Config＆Storageリソース

- Secret

- ConfigMap

- PersistentVolumeClaim

---
### Secret

- 機密情報を定義

  - パスワード、トークン、Keyなど

  - kubesec で暗号化

---
### ConfigMap

- Key-Valueでデータを保持

  - 設定情報とコンテナを分離

---
class: center, middle, blue
## Clusterリソース

---
### Clusterリソース

.zoom1[
- Namespace

- ServiceAccount

- Role/ClusterRole

- RoleBinding/ClusterRoleBinding

- Volume

- PersistentVolume

- Node
]

---
### Namespace

- リソースの分割

  - e.g. 開発者用、管理者用

  - アクセス制御

  - 仮想クラスタ

---
### StatefulSet

- データの永続化

- Podの管理

  - それぞれのPodに個別ID

  - 置き換え不可

---
### Volume

- ホスト上の領域をマッピング

- ファイルの保存

- コンテナ間のデータ共有

---

### PersistentVolume

- 永続化領域

- 利用には PersistentVolumeClaim(PVC) が必要

---
class: center, middle, blue
## Metadataリソース

---
### Metadataリソース

- CustomResourceDefinition

- LimitRange

- HorizontalPodAutoscaler

---
class: center, middle, inverse
# マニフェスト例

---
### Pod

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
### ReplicaSet

.zoom0[
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
### Deployment

.zoom0[
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
### Job

.zoom0[
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
### Secret

.zoom0[
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: sample-secret-single-env
spec:
  containers:
    - name: secret-container
      image: nginx:1.12
      env:
        - name: DB_USERNAME
          valueFrom:
            secretKeyRef:
              name: sample-db-auth
              key: username
```
]

---
### 書籍紹介

.left-half[
<center><img src="https://images-na.ssl-images-amazon.com/images/I/81nkS-qu9gL.jpg" width=90%></center>
]

.right-half[
<center><img src="http://image.gihyo.co.jp/assets/images/cover/2018/9784297100339.jpg" width=90%></center>
]

---
### 書籍紹介

.left-half[
<center><img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=90%></center>
]

.right-half[
<center><img src="https://images-na.ssl-images-amazon.com/images/I/71F%2BqeYXNgL.jpg" width=90%></center>
]

---
### 参考サイト

.zoom2[
公式サイト  
<u><https://kubernetes.io></u>

『Kubernetes完全ガイド』の付録マニフェスト  
<u><https://github.com/MasayaAoyama/kubernetes-perfect-guide></u>

今こそ始めよう！　Kubernetes入門  
<u><https://thinkit.co.jp/series/7342></u>
]

---
class: center, middle, blue
# Thank you!
