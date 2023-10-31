## Todo

- port?
- 为什么 `imagePullPolicy: IfNotPresent` 会对本地 docker 镜像有效
  - 当你在本地用 minikube 运行 k8s 时，镜像来源似乎有三个：public remote docker registry (Docker Offical)、local docker registry (Docker Deamon)、minikube docker registry、
  如果你不想让 minikube 从 public registry 拉取镜像，需要设置 `imagePullPolicy: Never`。但是这就会出现在 minikube registry 里也找不到镜像的情况，于是就会出现`ErrImageNeverPull`的错误，有两个解决办法
    - 需要执行`eval $(minikube docker-env)`命令，将你本地的 docker-cli 连接上 VM（minikube）的 docker daemon，然后再重新 build 镜像，这也就能把镜像加入到 minikube docker registry 里面了（https://stackoverflow.com/questions/52310599/what-does-minikube-docker-env-mean）
    - 执行 `minikube image load <image name>` 将镜像加入到 minikube 当中
  - https://medium.com/swlh/how-to-run-locally-built-docker-images-in-kubernetes-b28fbc32cc1d
  - https://stackoverflow.com/questions/42564058/how-can-i-use-local-docker-images-with-minikube
  - (如果本地没有，就用远端的)IfNotPresent: If you set the imagePullPolicy to IfNotPresent, Kubernetes will only pull the image when it doesn’t already exist on the node.
  - （忽略本地，永远用远端的）Always: With your imagePullPolicy set to Always, Kubernetes will always pull the latest version of the image from the container registry. 
  - （只用本地，永远不用远端）Never: If you set the imagePullPolicy to Never, there will be no attempts to pull the image. 
- 为什么无法直接访问，需要通过[特殊的地址访问](https://stackoverflow.com/a/40774861/508236)

## Q&A

- 如何记住 yaml 结构
  - ([https://k8syaml.com/](https://k8syaml.com/))
- labels 里可以有 app 这种 key 吗?
  - labels 似乎可以是任意的 key/value，但是用 app 似乎是一种约定俗成？
- 什么时候写 yml 的时候需要带上 `-` 符号
  - `-` 意味着列表中的一项 [https://www.reddit.com/r/ansible/comments/5jhff3/when_to_use_dash_in_yaml/](https://www.reddit.com/r/ansible/comments/5jhff3/when_to_use_dash_in_yaml/)
- `containerPort` 究竟有什么用？
- 删除 deployments 的顺序是什么？pods? service? deployments?
- 有 `apps/v1`，有 `apps/v2` 吗
- `apps/v1` 和 `v1` 有什么区别
- Ports
  - containerPort
  - port
  - targetPort
  - nodePort
- `Deployment` VS `Replicas` VS `Pods` VS `Container`
- 我怎么知道请求到了哪个 pod 里?
- Service 的 selector 是谁的 selector? pod 的？

## Command
- `kubectl delete -f [].yml`
- `kubectl apply -f [].yml`
- `kubectl describe pod [pod-name]`
- `kubectl logs [pod-name]`
- `kubectl logs --selector app=[]`
