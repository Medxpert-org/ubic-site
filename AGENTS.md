# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent（内容协作者、文档机器人、站点维护脚本）。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`ubic-site` 是 **UBIC Challenge 赛事系列**的官方静态站点与赛果归档，不是可运行的应用。核心资产是单文件站点 `index.html`（纯 HTML+内联 CSS，无构建、无后端、无依赖）与赛果报告 `首届UBIC-Challenge赛果报告_20260905.md`。它对外公布四条赛道、三级赛制、四维评审口径、参赛资格、奖项，并归档每一届赛果与可验证证书。

## 可用的工作命令

```bash
# 克隆并在本地预览站点
git clone https://github.com/Medxpert-org/ubic-site.git
cd ubic-site
python -m http.server 8000     # 访问 http://localhost:8000/index.html

# 查看首届赛果
cat "首届UBIC-Challenge赛果报告_20260905.md"

# 检查根目录文件清单与页面结构
ls -1
grep -oE '<section id="[^"]+"' index.html
```

前置依赖：仅需任意静态文件托管环境 / 浏览器；预览用 Python 3 即可，无第三方包。

## 约定（Do）

- 保持 `index.html` **单文件、零依赖、零构建**：不引入外部 JS/CSS 框架、不增加构建步骤。
- 新增赛果时，新建 `第N届UBIC-Challenge赛果报告_YYYYMMDD.md`，并在 `README.md`「赛果」段与 `llms.txt` 中追加链接。
- 改动赛事事实（赛道、赛制、评分口径、证书编号）前，先核对 `index.html` 与对应赛果报告，保持两处一致。
- 证书编号、四维分值须与赛果报告总榜单逐字一致。

## 禁止（Don't）

- 不要改动 `LICENSE`、`CODEOWNERS`，也不要改 `index.html` 页脚与赛果报告尾注中的权属 / 许可口径——**权属字段只由维护者变更**。
- 不要把内部试跑赛果表述为「公开赛名次」或「官方认证 / 资质」——结果效力须如实标注。
- 不要在仓库内提交任何密钥、令牌或个人隐私数据。
- 不要新增宣传性 / 品牌扩张表述；不要以 UBIC 名义发布未经授权的办赛 / 授牌声明。

## 边界

本仓只承载赛事**展示与赛果归档**：不实现评分引擎、不托管在线报名、不签发证书。验签逻辑与评分工具在治理工具链（如 governance MCP）侧，不在本仓。
