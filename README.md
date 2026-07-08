# Argosbx-mini

🚀 一行命令安装 Vless-tcp-reality-vision 科学上网节点

> 基于 [yonggekkk/argosbx](https://github.com/yonggekkk/argosbx) 深度精简，从 2324 行砍到 495 行，**减少 78% 代码量**，只保留最核心、最好用的功能。

---

## 📊 精简版 vs 原版对比

| 对比项 | 原版 argosbx | 精简版 mini |
|--------|-------------|-------------|
| 代码行数 | 2324 行 | **495 行** |
| 缩减比例 | — | **78%** |
| 支持的协议 | 12+ 种 | **仅 1 种** (Vless-tcp-reality-vision) |
| 安装复杂度 | 高（选项多、容易出错） | **低（一键搞定）** |
| 运行资源占用 | 较多 | **更少** |

---

## ✨ 保留的核心功能

- ✅ **Xray 内核** — 自动下载最新正式版，一键更新
- ✅ **Reality 加密** — 自动生成 X25519 密钥对，安全无忧
- ✅ **UUID 自动生成** — 无需手动填写
- ✅ **三种进程管理** — systemd / OpenRC / crontab，适配各种系统
- ✅ **IPv4 + IPv6 双栈** — 自动检测并显示可用的 IP
- ✅ **三种节点格式** — 同时输出 VLESS URI、Sing-box JSON、Clash YAML
- ✅ **五个快捷命令** — `list` / `upx` / `res` / `rep` / `del`，方便管理
- ✅ **无交互安装** — 设置几个参数就能全自动跑完

## ❌ 删除的不需要的功能

- ❌ Sing-box 内核（只用 Xray，更稳定）
- ❌ Hysteria2 / TUIC / AnyTLS / Shadowsocks / Vmess / Vless-ws / Vless-xhttp（只留最稳的一个）
- ❌ Argo Tunnel（Cloudflared）（不需要伪装 CDN）
- ❌ WARP 集成（不需要）
- ❌ 订阅服务（不需要）
- ❌ Hysteria2 跳跃端口（不需要）

---

## 🎯 什么是 Vless-tcp-reality-vision？

简单来说，这是目前**最稳、最快、最难被封锁**的协议之一：

- **Vless** — 一种轻量级传输协议，速度快
- **TCP** — 使用最常见的 TCP 网络连接，兼容性好
- **Reality** — 一种新型加密方式，比传统的 TLS/SSL 更难被检测
- **Vision** — 支持 UDP 转发，可以加速游戏和视频会议

效果就是：**速度快、延迟低、不容易被封**。

---

## 📋 系统要求

### 支持的系统

| 类型 | 支持的发行版 |
|------|-------------|
| Debian 系 | Debian 10+, Ubuntu 18.04+, Kali |
| RedHat 系 | CentOS 7+, RHEL, Fedora |
| Alpine | Alpine Linux 3.x |

### 支持的 CPU 架构

| 架构 | 说明 |
|------|------|
| **amd64 / x86_64** | 最常见的 PC 和云服务器（AWS t3, Google Cloud n1 等） |
| **arm64 / aarch64** | ARM 服务器（Oracle ARM, AWS Graviton, 树莓派 4 等） |

### 需要的权限

- **root 用户**（或能用 sudo 提权）
- 开放的互联网连接（能访问 GitHub、Google 等）

### 推荐的配置

- 内存：≥ 512MB（推荐 1GB 以上）
- 硬盘：≥ 1GB 可用空间
- 网络：能正常访问外网

---

## 🔧 一键安装

### 方法一：最简单，啥都不用改

直接把下面这行代码复制到终端（SSH）里回车：

```bash
bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

**它会做什么？**

1. 自动检测你的系统是什么（Debian / CentOS / Alpine）
2. 自动安装需要的依赖（curl、openssl、iptables 等）
3. 自动下载最新版的 Xray 内核
4. 自动生成 UUID（节点的唯一身份证）
5. 自动生成 Reality 密钥对（加密用的钥匙）
6. 随机选一个端口（10000-65535 之间）
7. 自动配置并启动服务
8. 安装完成后显示节点信息

> ⏱️ 整个过程大约 1-3 分钟，取决于网速。

---

### 方法二：指定端口

如果你想用特定的端口（比如 443），加个参数：

```bash
vlpt=yes port_vl_re=443 bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

**常用端口参考：**

| 端口 | 说明 |
|------|------|
| 443 | HTTPS 标准端口，最不容易被拦截 |
| 8443 | 备用 HTTPS 端口 |
| 2053 | Cloudflare 端口 |
| 2083 | Cloudflare 端口 |
| 任意 | 1024-65535 之间的数字都可以 |

> ⚠️ **注意：** 如果用 443 或 80 这种常用端口，确保服务器上没跑其他 Web 服务（比如 Nginx、Apache）。

---

### 方法三：指定域名

Reality 需要一个"伪装域名"，让流量看起来像在访问正常的网站。默认用 `apple.com`，你也可以自己改：

```bash
vlpt=yes reym=google.com bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

**推荐使用的域名：**

| 域名 | 说明 |
|------|------|
| `google.com` | 最推荐，全球都能访问 |
| `apple.com` | 默认值，也很好 |
| `microsoft.com` | 微软官方域名 |
| `cloudflare.com` | CDN 厂商域名 |
| `facebook.com` | Meta 旗下 |
| `youtube.com` | Google 旗下 |

> 💡 **原理：** 你的流量会伪装成在访问这些大网站的 HTTPS 连接，防火墙很难区分。

---

### 方法四：组合使用

端口和域名可以同时指定：

```bash
vlpt=yes port_vl_re=443 reym=google.com bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

---

## 📖 安装后的操作

### 第一步：重新连接 SSH

安装完成后，脚本会在你的系统里注册一个快捷命令 `agsbx`。但要让它生效，你需要：

**断开当前的 SSH 连接，然后重新连进去。**

或者在当前终端执行：
```bash
source ~/.bashrc
```

### 第二步：查看节点信息

```bash
agsbx list
```

你会看到类似这样的输出：

```
*********************************************************
Argosbx-mini 输出节点配置如下：

💣【 Vless-tcp-reality-vision 】节点信息如下：

vless://xxxx-xxxx-xxxx-xxxx@1.2.3.4:443?...

    // Sing-box JSON 格式

- name: xxx-reality-vision-xxx               # Clash 格式
  type: vless
  server: 1.2.3.4
  ...
```

这里提供了**三种格式**，对应不同的客户端：

| 格式 | 适用客户端 | 说明 |
|------|-----------|------|
| **VLESS URI** | 任何支持 VLESS 的客户端 | 直接复制整行粘贴 |
| **Sing-box JSON** | Sing-box / Hiddify / Nekobox | JSON 格式，导入配置文件 |
| **Clash 格式** | Clash / Clash Meta / Mihomo | YAML 格式，导入配置文件 |

---

## 🛠️ 日常命令速查

安装完成后，你可以在任何地方用以下命令管理你的节点：

### 查看所有节点信息

```bash
agsbx list
```

显示当前运行的节点配置和链接。

---

### 更新 Xray 内核

```bash
agsbx upx
```

会自动下载最新的 Xray 正式版并替换旧版本，然后重启服务。

> 💡 **什么时候需要更新？**
> - 发现旧版本有 bug
> - Xray 发布了新特性
> - 定期维护（建议每月一次）

---

### 重启服务

```bash
agsbx res
```

停止当前服务，然后重新启动。

> 💡 **什么时候需要重启？**
> - 修改了配置后
> - 服务卡住了
> - 系统更新后

---

### 重置并重新安装

```bash
agsbx rep
```

会清除当前所有配置（密钥、端口、UUID），然后从头开始安装。

> 💡 **什么时候需要重置？**
> - 想换一个新的端口
> - 想换一个域名
> - 配置乱了想重来
> - 想重新生成密钥对

重置后**会自动开始安装**，不需要再跑一遍安装命令。

---

### 卸载

```bash
agsbx del
```

会彻底删除：
- Xray 内核文件
- 所有配置文件（密钥、UUID、端口等）
- 服务注册（systemd / OpenRC）
- 定时任务（crontab）
- 快捷命令（agsbx）

> ⚠️ **卸载后所有数据都会丢失，无法恢复！**

---

## 🔑 环境变量详解

安装时可以通过设置环境变量来自定义行为：

| 变量名 | 作用 | 可选值 | 默认值 |
|--------|------|--------|--------|
| `vlpt` | 启用 Vless-tcp-reality-vision 协议 | `yes` 或 `no` | `yes` |
| `uuid` | 自定义 UUID（节点的身份证号） | 32位十六进制字符串 | 自动生成 |
| `port_vl_re` | 自定义端口号 | 1-65535 | 随机 10000-65535 |
| `reym` | 自定义 Reality 伪装域名 | 任意有效域名 | `apple.com` |
| `oap` | 一键开放所有防火墙规则 | `yes` 或 `no` | 关闭 |
| `ippz` | 选择输出的 IP 类型 | `4`(IPv4) / `6`(IPv6) | 自动 |

### 示例：自定义 UUID

```bash
uuid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

> 💡 UUID 格式：`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`（8-4-4-4-12 的十六进制数字）

---

## 📱 客户端使用指南

### 支持的客户端

| 客户端 | 平台 | 推荐度 | 说明 |
|--------|------|--------|------|
| **Hiddify Next** | Win / Mac / Linux / Android / iOS | ⭐⭐⭐⭐⭐ | 全能型，支持所有协议 |
| **Nekobox** | Android / iOS | ⭐⭐⭐⭐ | 轻量好用 |
| **Sing-box** | 全平台 | ⭐⭐⭐⭐ | 性能好，配置灵活 |
| **Clash Meta (Mihomo)** | Win / Mac / Linux | ⭐⭐⭐⭐ | 适合高级用户 |
| **V2RayNG** | Android | ⭐⭐⭐ | 老牌稳定 |
| **Streisn** | 全平台 | ⭐⭐⭐ | 开源免费 |

### 导入节点的方法

#### 方法 A：复制链接（最简单）

1. 运行 `agsbx list` 获取 VLESS URI
2. 复制以 `vless://` 开头的那一整行
3. 打开你的客户端
4. 粘贴 → 自动识别配置

#### 方法 B：手动填写

1. 运行 `agsbx list` 查看各项参数
2. 在客户端里手动填入：
   - **地址**：你的服务器 IP
   - **端口**：安装时指定的端口（默认随机）
   - **UUID**：安装时生成的 UUID
   - **流控**：`xtls-rprx-vision`
   - **传输协议**：`tcp`
   - **TLS**：开启 Reality
   - **SNI**：你指定的域名（如 google.com）
   - **公钥**：Public Key
   - **短 ID**：Short ID

---

## 🔒 安全须知

### 建议

1. **定期更新内核** — 运行 `agsbx upx` 保持最新版本
2. **使用强 UUID** — 不要用默认的，自己生成一个
3. **选择合适的域名** — 用你能稳定访问的大站域名
4. **防火墙设置** — 只开放必要的端口

### 注意事项

- ⚠️ Reality 协议虽然很安全，但请遵守当地法律法规
- ⚠️ 不要在公共场合分享你的节点链接
- ⚠️ 密钥对（private_key）请妥善保管，泄露等于节点被破解
- ⚠️ 如果服务器被攻击或节点被封，运行 `agsbx rep` 重新安装

---

## 🐛 常见问题

### Q1: 提示 "未安装argosbx-mini"

**原因：** 你没有设置 `vlpt=yes` 就直接运行脚本。

**解决：**
```bash
vlpt=yes bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

---

### Q2: 安装后 `agsbx` 命令找不到

**原因：** 还没重新加载环境变量。

**解决：**
```bash
source ~/.bashrc
# 或者直接断开 SSH 重新连接
```

---

### Q3: 节点连不上

**排查步骤：**

1. 检查服务器 IP 是否正确：`agsbx list`
2. 检查端口是否被防火墙拦截：`curl -v telnet://你的IP:端口`
3. 检查服务是否在运行：`agsbx list` 看状态
4. 重启试试：`agsbx res`
5. 查看日志：`systemctl status xr`

---

### Q4: 更新内核失败

**原因：** GitHub 访问慢或被墙。

**解决：** 等网络好的时候再试，或者手动下载：
```bash
agsbx upx
```

---

### Q5: 想换端口怎么办？

运行重置命令，安装时指定新端口：
```bash
agsbx rep
# 然后
vlpt=yes port_vl_re=新端口 bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

---

### Q6: 怎么知道服务器支持 IPv6？

```bash
curl -6 -s https://icanhazip.com
```

如果有返回 IP 地址，就支持 IPv6。

---

### Q7: 安装时提示 "不支持的架构"

**原因：** 你的 CPU 架构不在支持列表中（目前只支持 amd64 和 arm64）。

**解决：** 确认你的系统架构：
```bash
uname -m
```

---

## 📁 文件结构

安装后相关文件的位置：

| 路径 | 说明 |
|------|------|
| `/root/agsbx/` | 脚本主目录 |
| `/root/agsbx/xray` | Xray 内核程序 |
| `/root/agsbx/xr.json` | Xray 配置文件 |
| `/root/agsbx/uuid` | 存储 UUID |
| `/root/agsbx/port_vl_re` | 存储端口号 |
| `/root/agsbx/ym_vl_re` | 存储域名 |
| `/root/agsbx/xrk/private_key` | Reality 私钥 |
| `/root/agsbx/xrk/public_key` | Reality 公钥 |
| `/root/agsbx/xrk/short_id` | Reality Short ID |
| `/root/bin/agsbx` | 快捷命令 |
| `/etc/systemd/system/xr.service` | systemd 服务文件 |

---

## 🔄 从原版 argosbx 迁移

如果你之前用的是原版 argosbx，可以先卸载再装 mini：

```bash
# 1. 卸载原版
bash <(curl -Ls https://raw.githubusercontent.com/yonggekkk/argosbx/main/argosbx.sh) del

# 2. 等待几秒确保清理干净
sleep 5

# 3. 安装精简版
vlpt=yes bash <(curl -Ls https://raw.githubusercontent.com/h1151449095/argosbx-mini/main/argosbx-mini.sh)
```

---

## 📜 许可证

MIT License

你可以自由使用、修改和分发此脚本。

---

## 🙏 致谢

- 原项目作者：**[yonggekkk](https://github.com/yonggekkk)**
- Xray 内核：**[XTLS/Xray-core](https://github.com/XTLS/Xray-core)**
- Reality 协议设计：**[matt**](https://github.com/matt81033)**

---

## 📞 反馈与支持

有问题或建议？欢迎在 [GitHub Issues](https://github.com/h1151449095/argosbx-mini/issues) 提交。
