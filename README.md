# Argosbx-mini

精简版 Vless-tcp-reality-vision 一键安装脚本

基于 [yonggekkk/argosbx](https://github.com/yonggekkk/argosbx) 魔改精简，仅保留 **Vless-tcp-reality-vision** 协议。

## 对比

| 指标 | 原版 argosbx | 精简版 mini |
|------|-------------|------------|
| 代码行数 | 2324 行 | 495 行 |
| 缩减比例 | — | **78%** |
| 协议数量 | 12+ 种 | **1 种** (Vless-tcp-reality-vision) |

## 保留功能

- ✅ Xray 内核（自动下载更新）
- ✅ Reality 密钥对自动生成（X25519）
- ✅ UUID 自动生成
- ✅ systemd / OpenRC / crontab 三种进程管理
- ✅ IPv4/IPv6 双栈检测
- ✅ 节点链接输出（VLESS URI + Sing-box 格式 + Clash 格式）
- ✅ `list` / `upx` / `res` / `rep` / `del` 五个快捷命令
- ✅ 环境变量驱动无交互安装

## 删除功能

- ❌ Sing-box 内核
- ❌ Hysteria2 / TUIC / AnyTLS / Shadowsocks / Vmess / Vless-ws / Vless-xhttp
- ❌ Argo Tunnel (Cloudflared)
- ❌ WARP 集成
- ❌ 订阅服务 (websbx)
- ❌ Hysteria2 跳跃端口

## 快速安装

### 随机端口安装

```bash
bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

### 指定端口

```bash
vlpt=yes port_vl_re=443 bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

### 指定域名

```bash
vlpt=yes reym=google.com bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

## 常用命令

| 命令 | 说明 |
|------|------|
| `agsbx list` | 查看节点信息 |
| `agsbx upx` | 更新 Xray 内核 |
| `agsbx res` | 重启服务 |
| `agsbx rep` | 重置并重新安装 |
| `agsbx del` | 卸载脚本 |

## 环境变量

| 变量 | 说明 | 默认值 |
|------|------|--------|
| `vlpt` | 启用 Vless-tcp-reality-vision | yes |
| `uuid` | 自定义 UUID | 自动生成 |
| `port_vl_re` | 自定义端口 | 随机 10000-65535 |
| `reym` | 自定义 Reality 域名 | apple.com |
| `oap` | 开放所有防火墙端口 | 关闭 |
| `ippz` | 选择 IPv4(4) 或 IPv6(6) 输出 | 自动 |

## 支持系统

- Debian / Ubuntu / Kali
- CentOS / RHEL / Fedora
- Alpine Linux
- ARM64 / AMD64 架构

## 注意事项

- 需要 root 权限运行
- 建议先用 `agsbx del` 清理旧环境
- 安装完成后需**重新连接 SSH** 才能使 `agsbx` 快捷命令生效
- 如果脚本无法访问 GitHub，可设置 DNS fallback 或使用 `oap=yes` 开放防火墙

## 许可证

MIT License

## 原项目

[yonggekkk/argosbx](https://github.com/yonggekkk/argosbx)
