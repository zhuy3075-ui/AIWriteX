# AIWriteX

AIWriteX 是一个基于 CrewAI、AIForge、FastAPI、PyWebView、GrapesJS 与 Monaco Editor 的本地智能内容创作工具。项目支持热点选题、资料检索、文章生成、模板排版、配图设计、文章管理和微信公众号发布配置。

本仓库已整理去除官网、店铺、联系方式、商业合作、下载引导、示例预览跳转等推广导流内容。版权、许可证和第三方依赖声明仍按原项目要求保留。

## 功能概览

- 多智能体写作流程：研究、写作、审核、排版协作生成内容。
- 热点与搜索辅助：结合本地配置和 AIForge 搜索能力补充资料。
- 模板排版：内置多分类 HTML 模板，支持压缩模板输入以降低 token 消耗。
- 配图设计：支持封面图、内容配图和图片资源管理。
- 文章管理：支持文章保存、预览、编辑和发布流程管理。
- 平台适配：当前重点支持微信公众号 HTML 排版与发布配置。
- 桌面界面：通过 PyWebView 提供本地 GUI，也可使用命令行流程。

## 配置说明

主要配置文件：

- `src/ai_write_x/config/config.yaml`
- `src/ai_write_x/config/aiforge.toml`

常用配置项：

| 配置项 | 说明 |
| --- | --- |
| `platforms` | 热点平台权重配置 |
| `publish_platform` | 发布目标平台，默认 `wechat` |
| `wechat` | 微信公众号 AppID、AppSecret、作者和群发配置 |
| `api` | 主写作模型提供商、模型、API Key 和 API 地址 |
| `img_api` | 图片生成或随机图配置 |
| `use_template` | 是否使用内置 HTML 模板 |
| `template_category` | 模板分类 |
| `template` | 指定模板文件名 |
| `use_compress` | 是否压缩模板内容 |
| `aiforge_search_max_results` | 搜索最大返回结果数 |
| `aiforge_search_min_results` | 搜索最小返回结果数 |
| `min_article_len` | 生成文章最小字数 |
| `max_article_len` | 生成文章最大字数 |
| `auto_publish` | 是否自动发布 |
| `article_format` | 输出格式，支持 HTML、Markdown、txt |
| `format_publish` | 非 HTML 格式发布前是否格式化 |

运行前请根据自己的模型服务和发布平台填写必要的 API Key、AppID、AppSecret 等敏感配置。不要把真实密钥提交到仓库。

## 开发运行

```shell
pip install uv
uv venv
uv pip install -r requirements.txt
```

启动桌面界面：

```shell
python .\main.py
```

启动无界面写作流程：

```shell
python -m src.ai_write_x.crew_main
```

## 目录结构

```text
src/ai_write_x/
  adapters/          平台适配
  config/            默认配置与配置管理
  core/              多智能体工作流核心
  creative/          创意变换能力
  license/           授权接口占位实现
  utils/             通用工具
  web/               FastAPI 与 Web UI
knowledge/templates/ 内置文章模板
tests/               测试用例
output/              运行输出目录
logs/                日志目录
```

## 常见注意事项

- 微信发布接口需要在微信后台配置 IP 白名单。
- 未认证账号和个人主体账号可能无法完成自动发布，只能生成草稿后手动处理。
- 微信文章环境会移除部分 CSS、脚本和 HTML 标签，复杂模板需要实际预览。
- 建议优先在本地使用示例配置验证写作、排版和保存流程，再开启自动发布。

## 许可证

本项目保留原项目的许可证与附加声明文件：

- [LICENSE](./LICENSE)
- [NOTICE](./NOTICE)
- [docs/license.txt](./docs/license.txt)

使用、修改、分发或再次发布前，请阅读并遵守这些文件中的条款。
