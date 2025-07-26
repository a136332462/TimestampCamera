# 时间戳相机 (Timestamp Camera) - 说明文档

## 项目概述

这是一个基于 Next.js 和 React 构建的时间戳相机 Web 应用，允许用户为图片添加时间戳、GPS 信息、签名和 Logo 等水印。项目采用 TypeScript 开发，支持多语言国际化，并提供了丰富的自定义选项。

🌐 **在线体验**: [https://www.timestampcameras.com](https://www.timestampcameras.com)

### 产品特色

- **毫秒级精度**: 支持毫秒级时间戳显示
- **多层水印系统**: 时间戳、GPS 定位、自定义签名和 Logo
- **高度自定义**: 64 种时间格式，完全可调整的字体和颜色
- **多设备体验**: 上传、拍照、二维码扫描、移动端友好、自动保存设置
- **免费使用**: 提供免费版本，无需注册即可使用

## 架构


## 详解

### 1. (index.tsx)

**功能**: 整个应用的主入口组件，负责状态管理和组件协调

**主要特性**:
- 统一状态管理（图片、水印文本、时间格式、GPS 信息等）
- 动态组件导入优化性能
- 图片下载功能
- 水印位置计算和自定义定位

**核心状态**:
```typescript
interface HomeState {
  image: string | null;
  watermarkText: string;
  timeFormat: string;
  address: string;
  fontStyle: FontStyle;
  position: string;
  gps: GPSInfoValue;
  rotate: number;
  fileName: string;
  signature: string;
  logo: string | null;
  vertical: boolean;
  watermarkVisible: boolean;
  watermarkPositions: WatermarkPositions;
}
```

### 2. MainFunctionSection.tsx

**功能**: 主要功能操作区域，包含所有设置选项和预览

**布局结构**:
- **左侧**: 功能设置面板
  - 文件上传
  - 水印可见性切换
  - 时间水印设置
  - 字体样式设置
  - 水印位置选择
  - 图片旋转
  - 签名输入
  - GPS 信息
  - Logo 上传
  - 下载文件名设置
- **右侧**: 实时预览区域
  - 图片预览
  - 水印效果展示
  - 下载按钮

### 3. ImagePreviewArea.tsx

**功能**: 图片预览和水印渲染的核心组件

**主要特性**:
- 实时水印预览
- 支持拖拽自定义水印位置
- 多种预设位置（左上、右上、居中、左下、右下等）
- 支持垂直文本显示
- 水印可见性控制
- 图片旋转效果

**水印类型**:
- 时间戳水印
- 地址信息水印
- 签名水印
- Logo 水印
- GPS 信息水印

### 4. FileUpload.tsx

**功能**: 文件上传和相机拍照功能

**支持功能**:
- 本地文件上传（支持拖拽）
- 相机拍照
- 远程上传（二维码扫描）
- 文件大小限制（20MB）
- 多种文件格式支持
- 移动端优化

**技术特性**:
- 使用 `navigator.mediaDevices.getUserMedia` 实现相机功能
- Canvas 截图处理
- 文件类型验证
- 上传状态管理

### 5. TimeWatermark.tsx

**功能**: 时间水印设置和格式化

**时间格式支持**:
- 标准格式：`YYYY-MM-DD HH:mm:ss`
- 毫秒格式：`YYYY-MM-DD HH:mm:ss.SSS`
- 12小时制：`YYYY-MM-DD hh:mm:ss A`
- 中文格式：`YYYY年MM月DD日 HH:mm:ss`
- 文件友好格式：`YYYYMMDD_HHmmssSSS`
- ISO 格式：`YYYY-MM-DDTHH:mm:ss.SSSZ`

**功能特性**:
- 实时时间预览
- 自动更新时间
- 自定义时间格式
- 地址信息添加

### 6. FontStyleSettings.tsx

**功能**: 字体样式和显示效果设置

**可配置选项**:
- **字体选择**: Arial、Noto Sans、微软雅黑等 13 种字体
- **颜色选择**: 支持任意颜色选择
- **字体大小**: 10-64px 可调
- **透明度**: 0-100% 可调
- **文本方向**: 水平/垂直显示切换

### 7. GPSInfo.tsx

**功能**: GPS 地理位置信息设置

**特性**:
- 自动定位功能
- 手动输入坐标
- 支持海拔和速度信息
- 定位权限处理
- 错误状态管理

**GPS 信息包含**:
- 纬度 (Latitude)
- 经度 (Longitude)
- 海拔 (Altitude)
- 速度 (Speed)

### 8. HeroSection.tsx

**功能**: 首页英雄区域，展示产品核心价值

**设计特性**:
- 动态渐变背景
- 3D 星空效果
- 响应式设计
- 动画交互效果
- 多语言支持

### 9. 辅助组件

#### WatermarkPositionSelector.tsx
- 水印位置预设选择
- 支持 9 种预设位置
- 自定义位置模式

#### FileRotate.tsx
- 图片旋转控制
- 90° 增量旋转
- 实时预览效果

#### SignatureInput.tsx
- 签名文本输入
- 实时预览
- 多语言支持

#### LogoUploader.tsx
- Logo 图片上传
- 预览功能
- 文件验证

#### DownloadFileName.tsx
- 下载文件名设置
- 自定义命名规则
- 文件扩展名处理

## 技术栈

### 前端框架
- **Next.js 14**: React 全栈框架
- **React 18**: 用户界面库
- **TypeScript**: 类型安全

### UI 组件库
- **shadcn/ui**: 现代化 UI 组件
- **Tailwind CSS**: 原子化 CSS 框架
- **Framer Motion**: 动画库

### 功能库
- **next-intl**: 国际化支持
- **qrcode.react**: 二维码生成
- **uuid**: 唯一标识符生成

### 开发工具
- **ESLint**: 代码质量检查
- **Prettier**: 代码格式化
- **TypeScript**: 类型检查

## 国际化支持

项目支持多语言，目前包含：
- 中文 (zh)
- 英文 (en)
- 日文 (ja)

翻译文件位于 `i18n/messages/` 目录下，按语言和功能模块组织。

## 性能优化

### 代码分割
- 使用 `dynamic` 导入非首屏组件
- 按需加载功能模块

### 状态管理
- 使用 `useMemo` 优化计算属性
- 使用 `useCallback` 优化事件处理
- 合理使用 `useRef` 避免重复渲染

### 图片处理
- Canvas 优化图片处理
- 文件大小限制
- 压缩和格式转换

## 浏览器兼容性

### 支持的功能
- 现代浏览器 (Chrome, Firefox, Safari, Edge)
- 移动端浏览器
- PWA 支持

### 特性检测
- GPS 定位功能
- 相机 API 支持
- 文件上传 API
- Canvas 支持

## 在线体验

🎯 **立即体验**: [https://www.timestampcameras.com](https://www.timestampcameras.com)

### 主要功能演示

根据 [Timestamp Camera 官网](https://www.timestampcameras.com) 展示的功能，该应用提供：

- **文件上传**: 支持图片/视频文件上传、拖拽、二维码扫描上传
- **相机拍照/录像**: 支持摄像头拍照/录像，自动保存设置
- **水印可见性切换**: 动态切换水印显示/隐藏
- **时间地址水印**: 支持 64 种时间格式，地址可以是位置、建筑名称等任意文本
- **字体样式设置**: 自定义字体、颜色、大小、不透明度、垂直或水平显示模式
- **水印位置选择**: 支持 7 个预设位置和自定义拖拽定位
- **文件旋转**: 支持图片/视频文件旋转，垂直和水平显示
- **签名/标签输入**: 添加签名、标签、项目名称等到照片
- **地理位置和 GPS 信息**: 自动获取位置信息，支持 GPS 坐标、海拔、速度等作为叠加层
- **Logo 上传**: 上传自定义图标作为水印（Logo/印章等）
- **自定义下载文件名**: 自定义下载文件名（时间/标签/位置/序列号）

## 部署说明

### 环境要求
- Node.js 18+
- pnpm 包管理器
- 支持的环境变量配置

### 构建命令
```bash
# 安装依赖
pnpm install

# 开发环境
pnpm dev

# 生产构建
pnpm build

# 启动生产服务
pnpm start
```

## 贡献指南

### 开发规范
- 使用 TypeScript 编写代码
- 遵循 ESLint 规则
- 组件使用函数式组件和 Hooks
- 支持国际化

### 代码结构
- 组件按功能模块组织
- 使用 TypeScript 接口定义类型
- 统一的错误处理机制
- 完善的注释文档

## 许可证

本项目采用 MIT 许可证，详见 LICENSE 文件。

---

## 相关链接

- 🌐 **官方网站**: [https://www.timestampcameras.com/](https://www.timestampcameras.com/)
- 📖 **产品博客**: [https://www.timestampcameras.com/blogs](https://www.timestampcameras.com/blogs)

## 支持的语言

- 🇺🇸 English
- 🇨🇳 中文
- 🇯🇵 日本語

---

*本文档详细介绍了时间戳相机应用的 Home 组件模块，包括组件架构、功能特性、技术实现和使用说明。如有疑问或需要补充，请联系开发团队。*
