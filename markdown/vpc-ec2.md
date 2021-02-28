# Amazon VPC を作成〜EC2 インスタンスを起動まで ①
  
## 知識定着のためハンズオンしてみた  
  
### 構成図    
![complete](/image/vpc/vpc.drawio.png)  

### VPC 作成

デフォルトで VPC が作成されているので新たに作成する。
ここでとりあえず東京リージョンを選択しとけ。

![default](/image/vpc/defaultvpc.png)

![createvpc](/image/vpc/createvpc.png)

- VPC の名前を入力
- CIDR ブロックを決める(あんまりわかってないがとりあえず最大範囲)
- テナンシーはデフォルトで AWS のリソースを占有する項目(基本いじらなくてよし)

![createvpc1](/image/vpc/create-vpc.png)

VPC 作成完了。

今こんな感じ。

![default](/image/vpc/vpc1.drawio.png)

### サブネットの作成

パブリックサブネットとプライベートサブネットを作成し、
VPC を複数のサブネットに分割する。

### パブリックサブネット作成

インターネットと通信可能。
![default](/image/vpc/public-sb.png)

- どの VPC 内にサブネットを作成するか選択
- サブネット名入力
- AZ 指定(今回は東京リージョンのを指定)
- CIDR ブロック指定

![create-pub-sub](/image/vpc/create-pub-sub.png)

### プライベートサブネット作成

インターネットと通信不可。NAT Gateway 使おう。
基本的にはパブリックサブネットと同じ

![private-sub](/image/vpc/private-sub.png)

![private-sub](/image/vpc/create-pri-sb.png)

サブネット作成完了。

今こんな感じ。
![default](/image/vpc/vpc2.drawio.png)

### インターネットゲートウェイ作成

こいつ作成しないとインターネットに接続できない。
デフォルトの物があるが新しく作成。

![default](/image/vpc/internet-gateway.png)

![default](/image/vpc/create-int-ga.png)
作成完了。

### インターネットゲートウェイを VPC にアタッチ

アクションから VPC にアタッチを選択
![default](/image/vpc/vpc-attach1.png)

アタッチしたい VPC を選択
![default](/image/vpc/vpc-attach2.png)

今こんな感じ。
![default](/image/vpc/vpc3.drawio.png)
