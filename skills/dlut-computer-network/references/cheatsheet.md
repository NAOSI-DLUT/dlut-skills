# 计算机网络速查

## 常用公式
- 时延 = 发送时延 + 传播时延 + 处理时延 + 排队时延
- 香农定理：C = W · log₂(1 + S/N)
- CRC 校验：生成多项式 G(x)，余数补零位数 = deg(G)

## 子网划分速查
- 主机数 = 2^(主机位数) - 2
- CIDR 块可用地址 = 2^(32 - 前缀长度) - 2

## TCP 状态速查
- CLOSED → SYN-SENT → ESTABLISHED
- ESTABLISHED → FIN-WAIT-1 → FIN-WAIT-2 → TIME-WAIT → CLOSED
- ESTABLISHED → CLOSE-WAIT → LAST-ACK → CLOSED

## Wireshark 常用过滤
- `ip.addr == 192.168.1.1`
- `tcp.port == 80`
- `http`
- `dns.qry.name contains "example"`
