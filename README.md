# analog-tutor · 大肥鱼模电导师

一个给 [DeepSeek Harness](https://github.com/deepseek-ai) 用的**项目级模电技能**：识别题型、走固定 SOP、按题生成检查清单，把“模电题怎么一步步做对”固化成可复用的工作流。

符号体系强制遵循**康华光**教材。

## 能力

- **8 类题型**：共射放大、共集/共基、负反馈判断、差分放大、运算电路、功率放大、波形产生、稳压电源。每类都有重点、思维通路、常见问法、固定步骤与易错点。
- **黑箱题降级路径**：只给端口数据（如两次输入输出测量）时不硬套内部 Q 点 SOP，差分放大内置“端口测量模式”。
- **多级与组合电路**：拆成单级，级间用前级 $R_o$、后级 $R_i$ 衔接。
- **按题生成检查清单**：只列命中项，通用项与题型项去重；零命中时明确写“本题无适用检查项”。
- **26 条高频错误模式**，分 concept / sop / formula / circuit / state / calculation 六类；配合个人错题本，同题再犯会标 ×2。
- **独立验证默认内部执行**：Python / SymPy 复核答案，但不占正文；用户要求时才展示。
- **ElectroLab 优先**：会话处于 ElectroLab Mode 时数值必须来自 solver；不可用则退回手算 + 复核并标注未仿真。
- 公式统一 LaTeX（`$...$` / `$$...$$`），渲染由宿主决定。

## 安装

克隆到你的项目根目录，技能会自动落在 `.dsh/skills/analog-tutor/`：

```bash
git clone git@github.com:Her-LingXiao/analog-tutor.git
```

也可以只复制 `.dsh/skills/analog-tutor/` 到已有项目的同名路径。

## 触发

直接用自然语言提问即可：

- “教我共射放大电路的 Q 点怎么算”
- “分析一下这个差分放大电路”
- “模电题：判断这个反馈的类型”
- “帮我看看这个运放电路，我算的增益对不对”

## 目录结构

```
.dsh/skills/analog-tutor/
├── SKILL.md                    # 入口：工作流路由
└── references/
    ├── sop-index.md            # 8 类题型 SOP
    ├── checklist.md            # 通用 + 分题型检查项
    ├── error-patterns.md       # 高频错误模式与归因
    └── user-errors.md          # 个人错题本（本地累积）
```

## 说明

- 适配 DSH 的项目级技能目录；未在其它宿主上验证。
- 题图看不清时会标“需要你补充”，不猜参数。
