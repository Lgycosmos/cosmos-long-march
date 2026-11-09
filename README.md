# 2026迎新晚会 · 重走长征路·青春再出发

沈阳工业大学信息科学与工程学院长征主题互动游戏。当前交付包含不依赖 chatgpt.site 的独立 Node/SQLite 服务与本地网页资源。

## 老师 Mac 运行包

完整解压老师演示包，双击“开始演示.command”。包内包含 Node22.23.4 的 Apple Silicon 与 Intel 运行时，无需安装 Node 或 npm。首次启动生成 data/管理员信息.txt。手机与电脑连接同一 Wi-Fi 后扫描大屏二维码，HTTP 使用点击模式。手机流量跨网参加需独立公网部署。

详细操作见 docs/TEACHER_MAC_CN.md。

## 独立服务器部署

部署包包含 server.mjs、public、drizzle、Dockerfile、compose.yaml 与 Caddyfile。配置实际域名和管理密码后部署，数据库使用持久卷。详见 docs/DEPLOYMENT_CHINA_CN.md。Docker及真实服务器部署尚未验收。

## 源码构建

使用 Node22.23.4 或兼容更新版本安装依赖后执行 npm run build:standalone。生成 dist-standalone。运行时只依赖 Node 内置模块；教师包的启动不联网下载资源。

主要页面为 /screen、/join、/admin，活动码通过 room 查询参数传递。服务端统一计分、排名、暂停与结算，保留身份和历史成绩，支持 CSV 导出。手机支持运动权限申请与点击备用方式。

## 网络及兼容性边界

- 旧 chatgpt.site 的大陆网络拦截尚未修复，不能作为国内正式入口。
- 独立包支持本机、同 Wi-Fi 与配置域名后的公网运行；没有服务器和域名时不会自动产生长期公网地址。
- 临时 localhost.run 转发仅供用户验证，电脑和转发进程必须持续在线，不等于长期稳定托管。
- Node22 官方运行时支持 macOS11+，建议 Safari16.4+或兼容的 Chrome/Edge。Mac、Safari、微信真机和500人并发尚未验收。
- 用户已要求停止追加测试，已有记录见交付的新版验证记录。

Worker相关代码保留用于已有托管版本，但不是当前国内独立部署所必需的运行环境。
