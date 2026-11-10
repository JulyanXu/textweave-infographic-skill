# TextWeave · 文织

**让内容决定画面。把一段文字，织成一张读得懂的信息图。**

[English](README.en.md) · [技能入口](skills/textweave/SKILL.md) · [20种风格实测画廊](examples/deep-learning/gallery.md) · [MIT License](LICENSE)

![TextWeave · 文织：从文本到信息图](docs/assets/hero.png)

TextWeave 是一套面向 Agent 的信息图创作技能。它把文本拆解为可表现的对象、动作和关系，依据内容选择版式，再融入艺术风格，组织完整生图提示词，并在生成后检查文字与图示。

适合科普推文、技术说明、培训材料、知识卡片，以及同一内容的多风格设计测试。

## 从文字开始，得到什么？

- **内容结构**：提取核心结论、信息层级、过程、对比和因果关系。
- **可画的内容物**：明确画什么对象、对象在做什么，以及它们如何连接。
- **完整设计方案**：将画幅、信息密度、主视觉、阅读顺序、字体和配色写进提示词。
- **可执行的生成与检查**：有可用生图工具时生成并检查；没有生图工具时交付可直接复制的完整提示词。

核心文件是 [`skills/textweave/SKILL.md`](skills/textweave/SKILL.md)。TextWeave 依靠所用 Agent 和其可访问的生图工具运行；仓库本身不提供独立模型、生成引擎或网站服务。

支持仅交付提示词、生成单张、多风格对照和多页系列四种模式。单张请求默认只生成一张；明确要求“全部风格”时，按库中的20个主风格族执行。

## 它怎样工作？

| 阶段 | Agent 要做的事 |
|---|---|
| 1. 读取文本 | 确认主题、读者需要理解的重点，以及必须准确保留的内容。 |
| 2. 补齐偏好 | 仅询问尚未明确的关键偏好，最多3项：画幅／用途、密度／张数、风格／版式。已有答案直接使用；用户授权自动选择时直接继续。 |
| 3. 具体化语义 | 把抽象表述转换为对象、动作、关系和必要标注，识别哪些内容适合图像表达。 |
| 4. 选择版式 | 根据内容采用流程、对比、分层剖面、中心放大、时间线、分镜或编辑式图文等结构。 |
| 5. 融入风格 | 将图像媒介、色彩、字体、材质和构图统一为选定的视觉语言。 |
| 6. 生成与修正 | 调用可用生图工具，检查错字、漏句、标签、箭头、比例与画面完整性；每张最多2轮针对性修正，仍有问题时明确标出。 |

例如，同样介绍深度学习，解释训练过程时可以用“样本—模型—误差反馈”的流程；比较不同模型时可以用对照版式；讲述一次检测任务时可以用分镜。布局由需要解释的关系决定，文字块与插图共同承担信息。

### 一段典型对话

> **你：** 把这段“深度学习用于电芯缺陷检测”的文字做成信息图。
>
> **Agent：** 需要补充3项偏好：①用于什么场景、希望什么画幅？②希望做几张、信息量偏简洁还是详细？③有指定风格或版式吗？也可以交给我选择。
>
> **你：** 企业微信科普，9:16，一张，信息量中等。科学插图风格，版式你选。
>
> **Agent：** 我会以“电芯样本→神经网络→分类预测”为主视觉，将训练反馈与新图片推断分开表现，正文保留定义、案例、应用和验证说明，然后生成并检查。

如果你的第一条指令已包含这些偏好，Agent 可以直接继续设计。遇到必须核实的内容事实，会先明确不确定之处，不编造数据。

## 20种主要风格

这些风格是可组合的创作方向。每种方向同时约束图像、版式、字体与色彩，子分类和衍生形式可作为进一步细化的标签。

| 编号 | 风格 | 编号 | 风格 |
|---|---|---|---|
| 01 | 古典与学院派编辑 | 11 | 迷幻视觉 |
| 02 | 工艺美术与唯美主义 | 12 | 观念与超现实编辑插画 |
| 03 | 新艺术运动 | 13 | 漫画与幽默线描 |
| 04 | 装饰艺术 Art Deco | 14 | 新闻纪实摄影 |
| 05 | 俄罗斯构成主义 | 15 | 摄影蒙太奇与拼贴 |
| 06 | 包豪斯 | 16 | 科学插图 |
| 07 | 新字体设计 | 17 | 科学摄影与显微成像 |
| 08 | 瑞士国际主义 | 18 | 信息图与数据可视化 |
| 09 | 世纪中期编辑现代主义 | 19 | 后现代、新浪潮与实验设计 |
| 10 | 波普艺术 | 20 | 数字、三维与生成式视觉 |

![TextWeave风格探索概念示意](docs/assets/style-showcase.png)

*上图为项目营销概念示意。下方及完整画廊展示实际生成测试结果。*

## 同一段文案，20种实际生成结果

示例使用“深度学习与电芯表面缺陷检测”文案，统一9:16画幅、标题与六部分信息，按20个主要风格族各生成1张代表图。以下选取6张，完整提示词和全部结果见[实测画廊](examples/deep-learning/gallery.md)。

<table>
  <tr>
    <td align="center"><a href="examples/deep-learning/images/01-classical-editorial.png"><img src="examples/deep-learning/images/01-classical-editorial.png" width="220" alt="古典与学院派编辑风格深度学习信息图"></a><br><strong>01 古典与学院派</strong></td>
    <td align="center"><a href="examples/deep-learning/images/08-swiss-international.png"><img src="examples/deep-learning/images/08-swiss-international.png" width="220" alt="瑞士国际主义风格深度学习信息图"></a><br><strong>08 瑞士国际主义</strong></td>
    <td align="center"><a href="examples/deep-learning/images/10-pop-art.png"><img src="examples/deep-learning/images/10-pop-art.png" width="220" alt="波普艺术风格深度学习信息图"></a><br><strong>10 波普艺术</strong></td>
  </tr>
  <tr>
    <td align="center"><a href="examples/deep-learning/images/12-conceptual-surreal-editorial.png"><img src="examples/deep-learning/images/12-conceptual-surreal-editorial.png" width="220" alt="观念与超现实编辑插画风格深度学习信息图"></a><br><strong>12 观念与超现实</strong></td>
    <td align="center"><a href="examples/deep-learning/images/16-scientific-illustration.png"><img src="examples/deep-learning/images/16-scientific-illustration.png" width="220" alt="科学插图风格深度学习信息图"></a><br><strong>16 科学插图</strong></td>
    <td align="center"><a href="examples/deep-learning/images/20-digital-cgi-generative.png"><img src="examples/deep-learning/images/20-digital-cgi-generative.png" width="220" alt="数字三维生成式风格深度学习信息图"></a><br><strong>20 数字与三维</strong></td>
  </tr>
</table>

本轮覆盖20个主类，各1张代表性输出；衍生子类是可扩展标签，尚未逐一生成测试。这些结果用于观察视觉表达与阅读效果，不构成对所有生图模型的性能基准。

## 开始使用

### 通用 Agent

将 [`skills/textweave/SKILL.md`](skills/textweave/SKILL.md) 作为技能入口提供给 Agent，并保留其同目录下的参考资料。告诉 Agent 使用 TextWeave 处理你的文本即可。

### 手动安装到支持的技能目录

先取得仓库：

```bash
git clone https://github.com/JulyanXu/textweave-infographic-skill.git
cd textweave-infographic-skill
```

以下目录用于本地 CLI。请在仓库根目录执行与你所用 Agent 对应的一组命令。若目标目录已存在，请先检查并保留你自己的修改。

**Codex：**

```bash
mkdir -p ~/.agents/skills
cp -R skills/textweave ~/.agents/skills/textweave
```

**Claude Code：**

```bash
mkdir -p ~/.claude/skills
cp -R skills/textweave ~/.claude/skills/textweave
```

ChatGPT、Cowork及其他托管环境应遵循各自的技能安装机制，不直接套用上述本地目录。安装后的发现与调用方式以对应 Agent 的技能机制为准。参考：[OpenAI技能构建说明](https://learn.chatgpt.com/docs/build-skills)、[Claude Code技能文档](https://code.claude.com/docs/en/skills)。

生图能力取决于宿主环境中可用的工具；缺少工具时，仍可用 TextWeave 生成完整提示词，并明确本次未生成图片。

## 三种可复制用法

### 1. 自动选择风格与布局

```text
使用 TextWeave，把下面的文本制作成信息图。
请自动选择适合的画幅、密度、风格和版式，无需再询问这些偏好。
请具体设计图中的对象、动作与关系；有可用生图工具时生成并检查，没有时交付完整提示词。

文本：
[在这里粘贴你的文本]
```

### 2. 指定科学插图风格

```text
使用 TextWeave，将下面的内容做成1张9:16中文科学插图信息图，用于科普推文，信息密度中等。
请依据内容关系选择版式，明确主体结构、局部放大、标注和阅读顺序。
正文保持清楚，科学结构与箭头必须准确；不添加未经提供的数据。
生成后检查中文、标签对应和画面完整性，修正明显问题。

文本：
[在这里粘贴你的文本]
```

### 3. 对照测试多种风格

```text
使用 TextWeave，为同一段内容分别制作瑞士国际主义、波普艺术、科学插图、数字三维4种风格的信息图。
统一9:16画幅、标题、正文和信息量，每种风格各1张。
分别设计符合各风格的插图、版式、字体与配色，保持信息关系准确。
先整理每张完整提示词，再用可用生图工具生成、检查并修正。

文本：
[在这里粘贴你的文本]
```

## 使用边界与许可

中文精度、版式完整性和风格呈现取决于实际生图模型与输入内容。TextWeave 将检查与修正纳入流程，正式发布前仍应核对专有名词、数字及科学关系。无法查看输出时，应明确标为“未完成目检”。

精确图表使用确定性绘图工具，数值、刻度、比例与曲线保留为确定性图层，不交给生图模型重绘。精确科学结构和复杂关系也使用确定性绘图或已核对的结构原图。生图可用于独立配图或背景，再通过排版工具合成；无法合成时分开交付。

本仓库采用 [MIT License](LICENSE)。项目配图和案例图片为AI生成视觉示意，不代表真实检测数据或机构背书。
