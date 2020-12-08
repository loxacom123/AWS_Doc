# AWS
- [安裝必要軟體](#install)
- [設定AWS CLI](#config_aws_cli)
- [建立cluters](#create_cluters)

## <span id=install> 必要軟體 </span>
- [AWS CLI](#install_awscli)
- [eksctl](#install_eksctl)
- [kubectl](#install_kubectl)


## <span id=install_awscli> 安裝 AWS CLI </span>

**1.下載並安裝**
```shell=
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```

**2.查看安裝版本**
```shell=
$ aws --version
```

**3.輸出以下結果**
```shell=
$ aws-cli/2.0.57 Python/3.7.3 Linux/5.4.0-42-generic exe/x86_64.ubuntu.18
```

---

## <span id=install_eksctl> 安裝 eksctl </span>

**1.下載最新版本eksctl**
```shell=
$ curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```

**2.將二進位檔移至 ```/usr/local/bin```**
```shell=
$ sudo mv /tmp/eksctl /usr/local/bin
```

**3.查看安裝版本**
```shell=
$ ksctl version
```

**4.輸出以下結果**
```shell=
0.30.0
```

---

## <span id=install_kubectl> 安裝 kubectl </span>

**1.下載最新版本kubectl**
```shell=
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
```

**2.將檔案設為可執行**
```shell=
$ chmod +x ./kubectl
```

**3.將二進位檔移至 ```/usr/local/bin```**
```shell=
$ sudo mv ./kubectl /usr/local/bin/kubectl
```

**3.查看安裝版本**
```shell=
$ kubectl version --client
```

**4.輸出以下結果**
```shell=
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.2", GitCommit:"f5743093fd1c663cb0cbc89748f730662345d44d", GitTreeState:"clean", BuildDate:"2020-09-16T13:41:02Z", GoVersion:"go1.15", Compiler:"gc", Platform:"linux/amd64"}
```

---
## <span id=config_aws_cli> 設定AWS CLI </span>

```bash=
$ aws configure
AWS Access Key ID [None]: <AKIAIOSFODNN7EXAMPLE>
AWS Secret Access Key [None]: <wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY>
Default region name [None]: <region-code>
Default output format [None]: <json>
```

---

## <span id=create_cluters> 建立 Amazon EKS 叢集 </span>

- Fargate
- 託管節點
- 自我管理節點


### 託管節點
```
eksctl create cluster \
--name <my-cluster> \
--version <1.18> \
--region <us-west-2> \
--nodegroup-name <linux-nodes> \
--node-type t3.micro \
--nodes <3> \
--nodes-min <1> \
--nodes-max <4> \
--ssh-access \
--ssh-public-key <name-of-ec2-keypair> \
--managed
```

