本目录包含cadvisor重新修改编译后的dockerfile及其二进制文件。

功能更改：
将原来被动提供监控数据的工作方式改为主动上传数据到网关，并添加自定义采集模块。

cadvisor的版本为：v0.27.4

releases版本源码下载地址：https://github.com/google/cadvisor/archive/v0.27.4.tar.gz

构建说明：docker build -t singula/cadvisor .

使用说明：

1、启动网关
docker run --restart=always -d -p 9091:9091 prom/pushgateway:v0.4.0
pushgateway版本为：v0.4.0

2、运行cadvisor镜像
docker run -it -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -e PUSH_FREQ=120 -e  LOCAL_ADDR=xxxx -e  PUSH_ADDR=xxxx:9091 singula/cadvisor
其中，LOCAL_ADDR为采集终端的IP地址，PUSH_ADDR为pushgateway的地址，默认端口为9091，PUSH_FREQ用于设置采集的频率，120的单位为秒。

3、验证
浏览器中输入：LOCAL_ADDR/metrics，例如：xxxx:9091/metrics，网页中会得到大量的容器数据。

注：程序会从/tmp/sgl/userinfo文件中获取自定义的指标，文件须按照XXX:XXX的格式添加指标。