# AI 截图助手

一款桌面应用程序，通过截图并使用 AI（Google Gemini / OpenAI GPT）进行分析。具有隐蔽式浮窗显示和防截屏保护功能。

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyQt6](https://img.shields.io/badge/PyQt6-6.4+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg)

[English](README.md) | 中文

## 功能特性

- **多 AI 支持**：在 Google Gemini 和 OpenAI GPT 之间自由切换
- **智能截图**：支持区域选择或全屏截图
- **隐蔽浮窗**：半透明悬浮窗口，可与任何背景融合
- **防截屏保护**：浮窗对截屏工具不可见（仅限 Windows）
- **全局热键**：系统级快捷键，随时快速调用
- **多提示词**：配置多个 AI 提示词并快速切换
- **代码提取**：自动提取代码块并复制到剪贴板
- **流式响应**：实时显示 AI 响应内容

## 截图预览

> 截图即将添加

## 安装指南

### 环境要求

- Python 3.10 或更高版本
- Windows 10/11（防截屏功能需要）

### 安装步骤

1. 克隆仓库：
```bash
git clone https://github.com/yourusername/ai-screenshot-assistant.git
cd ai-screenshot-assistant
```

2. 创建虚拟环境（推荐）：
```bash
python -m venv venv
venv\Scripts\activate  # Windows
```

3. 安装依赖：
```bash
pip install -r requirements.txt
```

4. 配置应用：
```bash
copy model_config.example.json model_config.json
```

5. 编辑 `model_config.json` 并添加你的 API 密钥：
   - Gemini：从 [Google AI Studio](https://makersuite.google.com/app/apikey) 获取
   - GPT：从 [OpenAI Platform](https://platform.openai.com/api-keys) 获取

## 使用方法

### 启动应用

```bash
python main.py
```

### 默认快捷键

| 快捷键 | 功能 |
|--------|------|
| `Alt+Z` | 截图并发送到 AI 分析 |
| `Alt+Q` | 显示/隐藏浮窗 |
| `Alt+W` | 仅截图（添加到历史） |
| `Alt+V` | 清空截图历史 |
| `Alt+1-9` | 切换提示词 |
| `Alt+S` | 切换 AI 服务商 |
| `Alt+↑/↓` | 滚动浮窗内容 |

### 配置说明

应用使用 `model_config.json` 进行配置，可以设置：

- AI 服务商设置（API 密钥、模型、基础 URL）
- 网络代理设置
- 界面偏好（浮窗透明度、窗口大小）
- 自定义提示词
- 快捷键绑定

## 项目结构

```
ai-screenshot-assistant/
├── main.py                    # 应用入口
├── model_config.example.json  # 配置模板
├── requirements.txt           # Python 依赖
├── ai_assistant/
│   ├── core/
│   │   ├── config_manager.py  # 配置管理
│   │   ├── log_manager.py     # 日志系统
│   │   └── single_instance.py # 单实例锁
│   ├── services/
│   │   ├── ai/                # AI 服务抽象层
│   │   ├── gemini_api.py      # Gemini API 客户端
│   │   ├── gpt_api.py         # GPT API 客户端
│   │   └── network_utils.py   # 网络工具
│   ├── ui/
│   │   ├── overlay.py         # 隐蔽浮窗
│   │   ├── styles.py          # 应用样式
│   │   ├── theme/             # 设计令牌系统
│   │   └── ...                # 其他 UI 组件
│   └── utils/
│       ├── constants.py       # 应用常量
│       ├── hotkey_handler.py  # 全局热键管理
│       └── screenshot.py      # 截图工具
```

## 安全特性

### 防截屏保护

浮窗使用 Windows `SetWindowDisplayAffinity` API 和 `WDA_EXCLUDEFROMCAPTURE` 标志，使其对以下工具不可见：
- 截图工具（截图工具、ShareX 等）
- 屏幕录制软件
- 视频会议屏幕共享

> **注意**：此功能仅在 Windows 10/11 上有效。

### 隐蔽设计

浮窗设计追求低调隐蔽：
- 高透明度（可调节 50-255）
- 柔和的文字颜色
- 无可见边框和阴影
- 极简标题栏

## 开发指南

### 运行测试

```bash
python -m pytest tests/
```

### 代码风格

本项目遵循 PEP 8 规范。请使用 flake8 或 black 进行代码格式化。

## 参与贡献

欢迎贡献代码！请随时提交 Pull Request。

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 发起 Pull Request

## 开源许可

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

## 致谢

- [PyQt6](https://www.riverbankcomputing.com/software/pyqt/) - GUI 框架
- [Google Generative AI](https://ai.google.dev/) - Gemini API
- [OpenAI](https://openai.com/) - GPT API
- [pynput](https://pynput.readthedocs.io/) - 键盘监听
- [mss](https://python-mss.readthedocs.io/) - 屏幕截图

## 免责声明

本工具仅供个人效率提升使用。使用 AI 服务和屏幕截图功能时，请确保遵守您所在组织的政策和适用法律。
