# EdgeOne Monitoring Dashboard (EdgeOne 监控大屏)

本项目基于 [AcoFork/eo_monitor](https://github.com/afoim/eo_monitior) 二次开发，旨在提供直观的流量和请求分析。

## ✨ 主要功能

- **实时概览**：展示站点总请求数、总流量、总带宽等关键指标。
- **多维度分析**：
  - **流量分析**：总流量、请求流量、响应流量趋势
  - **带宽分析**：总带宽峰值、请求/响应带宽峰值
  - **请求分析**：请求数趋势
  - **性能分析**：L7 响应耗时趋势
  - **TOP 分析**：域名流量排行、URL 流量排行、URL 请求数排行
- **站点筛选**：支持选择特定站点或查看全部站点数据（包括 Pages 站点）
- **灵活查询**：
  - 支持快速切换时间范围（1小时、当天、七天、31天）
  - 数据粒度自动适配（无需手动选择）
- **响应式设计**：完美适配手机端和桌面端
- **个性化配置**：支持自定义站点名称、图标和备案号

## 🚀 快速部署

### 方式一：EdgeOne Pages (推荐)

1. Fork 本仓库到您的 GitHub 账号。
2. 前往 [腾讯云 EdgeOne 控制台](https://console.cloud.tencent.com/edgeone) 创建 Pages 项目。
3. 连接您的 GitHub 仓库。
4. 在 **环境变量 (Environment Variables)** 中添加以下配置：
   - `SECRET_ID`: 您的腾讯云 SecretId
   - `SECRET_KEY`: 您的腾讯云 SecretKey
   - `SITE_NAME`: (可选) 自定义大屏标题，默认为 "EdgeOne 监控大屏"
   - `SITE_ICON`: (可选) 自定义网页图标 URL
   - `ICP`: (可选) 备案号，如 "京ICP备12345678号"
5. 部署项目。

### 方式二：本地运行 / Node.js 环境

1. 克隆仓库：
   ```bash
   git clone https://github.com/MoForgt/edgeone-status
   cd edgeone-status
   ```

2. 安装依赖：
   ```bash
   npm install -g edgeone
   edgeone login
   ```

3. 配置密钥：
   - **方法 A (环境变量)**：创建 `.env` 文件或直接导出环境变量 `SECRET_ID` 和 `SECRET_KEY`。
   - **方法 B (文件配置)**：在项目根目录创建 `key.txt` 文件，内容格式如下（注意使用中文冒号）：
     ```text
     SecretId：您的SecretId
     SecretKey：您的SecretKey
     ```

4. 启动服务：
   ```bash
   edgeone pages dev
   ```

5. 访问 `http://localhost:8088`。

## 🔑 权限说明

使用的腾讯云访问密钥必须拥有 **EdgeOne 只读访问权限** (`QcloudTEOReadOnlyaccess`)。
请前往访问管理控制台创建和管理密钥（只需要 **编程访问**）：
- **国内版 (China Station)**: [https://console.cloud.tencent.com/cam/user/userType](https://console.cloud.tencent.com/cam/user/userType)
- **海外版 (International Station)**: [https://console.tencentcloud.com/cam/user/userType](https://console.tencentcloud.com/cam/user/userType)

## 📱 界面说明

### 顶部控制区
- **时间范围**：快速切换按钮（1小时、当天、七天、31天）
- **站点选择**：下拉框选择特定站点或全部站点

### 数据展示
- **KPI 卡片**：显示总流量、带宽峰值、请求数等关键指标
- **趋势图表**：展示各项指标的时序变化
- **TOP 排行**：域名、URL 的流量和请求数排行（一行三个）

### 底部信息
- 备案号（如已配置）
- 基于项目声明

## 🛠️ 技术栈

- **后端**：Node.js, Express, Tencent Cloud SDK
- **前端**：HTML5, Tailwind CSS, ECharts
- **部署**：Tencent Cloud EdgeOne Pages

## 📄 许可证

本项目基于 [AcoFork/eo_monitor](https://github.com/afoim/eo_monitior) 二次开发，采用 [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) 开源许可证。

根据 AGPL-3.0 许可证要求：
- 您可以自由使用、修改和分发本软件
- 修改后的代码必须以相同的 AGPL-3.0 许可证开源
- 如果您通过网络提供服务，用户有权获得完整的源代码
