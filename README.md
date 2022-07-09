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

## Command
- `kubectl delete -f [].yml`
