# EKS Tutorial

## 必要なパラメータ

- SecurityGroup ... ワーカーノードに追加するときに ID が必要
- VPC ... ワーカーノードグループテンプレートを起動するときに ID が必要
- Subnet ... ワーカーノードに追加するときは、ワーカーノードを起動するサブネットの ID が必要
- ノードインスタンス用のロール ... ノードグループの作成時に ID が必要
  - 以下管理ポリシーを使ってる
  - `policy/AmazonEKSWorkerNodePolicy`
  - `policy/AmazonEKS_CNI_Policy`
  - `policy/AmazonEC2ContainerRegistryReadOnly`

## 注意点

クラスターを作成したユーザが、Kubernetes クラスターの管理者として RBAC データベースに登録される。なので、`kubectl` の実行ユーザに注意（異なると, Unauthorized or access denied になる）

> When an Amazon EKS cluster is created, the IAM entity (user or role) that creates the cluster is added to the Kubernetes RBAC authorization table as the administrator (with system:master permissions. Initially, only hat IAM user can make calls to the Kubernetes API server using kubectl. For more information, see Managing users or IAM roles for your cluster. If you use the console to create the cluster, you must ensure that the same IAM user credentials are in the AWS SDK credential chain when you are running kubectl commands on your cluster.

## Reference

- [Getting started with the AWS Management Console - Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-console.html)
- [Launch a guest book application - Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/eks-guestbook.html)
