# 计算机网络实验工具

## Wireshark
- 官网：https://www.wireshark.org/
- 抓包步骤：选择网卡 → 设置捕获过滤 → 开始抓包 → 设置显示过滤 → 分析分组
- 常用导出：File → Export Specified Packets

## Cisco Packet Tracer / GNS3
- 用于模拟网络拓扑、配置路由器和交换机
- 注意保存拓扑文件（.pkt / .gns3）

## Socket 编程环境
- Linux/WSL: `gcc client.c -o client && ./client`
- Python: `socket` 标准库，无需额外安装
- Java: `java.net.Socket` / `ServerSocket`

## 本地测试
- `ping`、`tracert`/`traceroute`、`nslookup`、`netstat`、`curl`
