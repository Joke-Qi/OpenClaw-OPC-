# OpenClaw-OPC（每周日定时更新）

OpenClaw-OPC从搭建到开始帮我工作赚钱

**当前收支（- 616元）：**

**阿里云服务器2 核 (vCPU) 4 GiB——416元/年**

**智谱GLM4.7——1亿Token/200元/3个月**

## 一、安装OpenClaw

*<u>我这里使用 Xshell 8 、 Xftp 8 来远程访问和文件传输</u>*

### 1.查看服务器操作系统

```bash
cat /etc/os-release
```

以下是我的服务器信息，不同服务器对应的命令有所不同，这里以我的 **Alibaba Cloud Linux** 举例

```bash
NAME="Alibaba Cloud Linux"
VERSION="3 (OpenAnolis Edition)"
ID="alinux"
ID_LIKE="rhel fedora centos anolis"
VERSION_ID="3"
VARIANT="OpenAnolis Edition"
VARIANT_ID="openanolis"
ALINUX_MINOR_ID="2104"
ALINUX_UPDATE_ID="13"
PLATFORM_ID="platform:al8"
PRETTY_NAME="Alibaba Cloud Linux 3.2104 U13 (OpenAnolis Edition)"
ANSI_COLOR="0;31"
HOME_URL="https://www.aliyun.com/"
```

### 2.安装Node.js

```bash
# 安装 Node.js 官方源（最新版） 
curl -fsSL https://rpm.nodesource.com/setup_current.x | bash -

# 安装 Node.js
yum install -y nodejs

# 验证版本
node -v
npm -v
```

### 3.下载OpenClaw

```bash
# 全局安装最新版
npm install -g openclaw@latest
```

### 4.OpenClaw初始化配置

```bash
# 初始化配置
openclaw onboard
```

具体操作参考阿里百炼配置文档：[https://help.aliyun.com/zh/model-studio/openclaw](https://help.aliyun.com/zh/model-studio/openclaw?__dialog_id=581502529&__url_role=2)

### 5.启动服务并进入对话

```bash
# 启动服务
openclaw start

# 进入对话
openclaw tui
```

这里我使用命令行对话方式与龙虾进行交流，通过 Xftp 进行文件传输。

<u>*建议大家在龙虾的 .openclaw 专属文件夹中提前做好存储规划，划分对应文件夹功能，方便后续为龙虾配置查找机制，同时也为龙虾能形成良好的长期记忆打下基础*</u>

附：OpenClaw常见命令表

| 分类         | 命令                                 | 描述                                                         |
| ------------ | ------------------------------------ | ------------------------------------------------------------ |
| 初始化与安装 | `openclaw onboard`                   | 交互式向导（配置模型、通道、网关、工作区）                   |
| 初始化与安装 | `openclaw setup`                     | 初始化配置 + 工作区（非交互版）                              |
| 初始化与安装 | `openclaw configure`                 | 交互式配置向导（模型、通道、技能）                           |
| 卸载         | `openclaw uninstall`                 | 卸载 openclaw，清除本地数据                                  |
| 更新         | `openclaw update`                    | 更新 openclaw                                                |
| 网关管理     | `openclaw gateway status`            | 查看网关服务状态 + RPC 探活                                  |
| 网关管理     | `openclaw gateway start`             | 启动网关服务                                                 |
| 网关管理     | `openclaw gateway stop`              | 停止网关服务                                                 |
| 网关管理     | `openclaw gateway restart`           | 重启网关服务                                                 |
| 网关管理     | `openclaw gateway run`               | 直接在前台运行网关（调试用）                                 |
| 网关管理     | `openclaw gateway health`            | 获取网关健康信息                                             |
| 配置管理     | `openclaw config file`               | 显示当前配置文件完整路径                                     |
| 配置管理     | `openclaw config get <path>`         | 读取配置项                                                   |
| 配置管理     | `openclaw config set <path> <value>` | 修改配置项                                                   |
| 配置管理     | `openclaw config validate`           | 校验配置文件是否合法                                         |
| 诊断与状态   | `openclaw doctor`                    | 一键健康检查 + 自动修复；添加 `--fix` 自动解决               |
| 诊断与状态   | `openclaw status`                    | 显示会话健康状态和最近联系人                                 |
| 诊断与状态   | `openclaw health`                    | 从运行中的网关拉取健康数据                                   |
| 诊断与状态   | `openclaw logs`                      | 实时查看网关日志                                             |
| 其他高频操作 | `openclaw dashboard`                 | 打开网页控制面板场景：不小心把交互网页关闭，找回面板执行该命令或执行：`openclaw dashboard --no-open` 获取链接，复制到浏览器打开 |
| 其他高频操作 | `openclaw channels status`           | 查看已连接的聊天通道                                         |
| 其他高频操作 | `openclaw agent run`                 | 手动触发一次代理运行                                         |

## 二、初始化设置OpenClaw

