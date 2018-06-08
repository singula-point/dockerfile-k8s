Metrics server：
1、Metrics server是K8S集群资源使用情况的聚合器
2、从1.8版本开始，Metrics server默认可以通过kube-up.sh 脚本以deployment的方式进行部署，也可以通过yaml文件的方式进行部署
3、Metrics server收集所有node节点的metrics信息