# Xray 完整配置指南

Xray 是全功能代理平台，支持 VLESS、VMess、Trojan、Shadowsocks 等所有主流协议。

## Xray vs V2Ray

| 对比项 | Xray | V2Ray |
|--------|------|-------|
| VLESS Reality | 原生支持 | 需插件 |
| 性能 | 优化版 | 原始 |
| 配置格式 | 兼容 | 兼容 |

## 极速安装

```bash
bash <(curl -s https://raw.githubusercontent.com/XTLS/Xray-install/main/install-release.sh)
```

## 多协议配置模板

```json
{
  "inbounds": [
    {
      "port": 443,
      "protocol": "vless",
      "settings": {
        "clients": [{"id": "uuid-1", "flow": "xtls-rprx-vision"}],
        "decryption": "none"
      },
      "streamSettings": {
        "network": "tcp",
        "security": "reality",
        "realitySettings": {
          "dest": "www.microsoft.com:443",
          "serverNames": ["www.microsoft.com"],
          "privateKey": "your-private-key"
        }
      }
    },
    {
      "port": 10001,
      "protocol": "trojan",
      "settings": {"clients": [{"password": "your-password"}]}
    }
  ],
  "outbounds": [{"protocol": "freedom"}]
}
```

## 协议说明

### VLESS + Reality（推荐）- 最强抗封锁
### Trojan - 简单稳定，伪装 HTTPS 流量
### VMess - 历史最久，兼容性好

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
