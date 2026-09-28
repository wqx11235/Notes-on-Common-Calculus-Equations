# 常微分方程笔记

**Notes on Common Calculus Equations**

跟随 MIT 18.03《Differential Equations》整理的中文常微分方程笔记，使用 LaTeX 排版。
共 **13 章 / 109 页**，含 53 张讲义插图，以「几何直观 → 代数解法 → 模型应用」的方式串起一阶、二阶方程、傅里叶与拉普拉斯变换、线性方程组与非线性定性分析。

![LaTeX](https://img.shields.io/badge/LaTeX-pdfLaTeX-008080)
![TeX Live](https://img.shields.io/badge/TeX%20Live-2025-blue)
![Pages](https://img.shields.io/badge/%E9%A1%B5%E6%95%B0-109-orange)
![Chapters](https://img.shields.io/badge/%E7%AB%A0%E8%8A%82-13-green)
![Language](https://img.shields.io/badge/%E8%AF%AD%E8%A8%80-%E4%B8%AD%E6%96%87-red)

---

## 这份笔记的特点

- **几何直觉先行**：先画方向场与积分曲线，理解解的形状，再回头讲代数解法，而不是堆公式。
- **每个方法配一个真实模型**：牛顿冷却、受迫阻尼振动、逻辑斯蒂人口模型（含收割项收益分析）、双层温度系统、捕食者—被捕食者模型等。
- **覆盖数值解法**：Euler 法、误差分析、改进 Euler 法（步长改进 / 斜率改进）。
- **证明写得完整**：傅里叶系数的正交性、拉普拉斯卷积定理（二重积分换元）、本迪克松准则（用散度的曲线积分）、矩阵指数性质等均给出推导。
- **强调「什么时候用哪个方法」**：换元、积分因子、特征方程、变换法各自的适用边界都有交代。

## 章节总览

| 章 | 标题 | 起始页 | 主要内容 |
|:--:|:--|:--:|:--|
| 1 | 几何视角下的微分方程 | 6 | 方向场、等斜线作图法、积分曲线作图原理 |
| 2 | Euler 数值方法及推广 | 11 | Euler 迭代、误差的凹凸性分析、改进 Euler 法 |
| 3 | 一阶线性 ODE | 18 | 标准形式、温度模型、积分因子法、暂态解与稳态解 |
| 4 | 一阶方程换元法 | 22 | 尺度变换（无量纲化）、伯努利方程、一阶齐次方程 |
| 5 | 一阶自治方程 | 25 | 临界点（稳定/非稳定/半稳定）、逻辑斯蒂方程与收割 |
| 6 | 复数和复指数 | 30 | 极坐标形式、欧拉公式、复指数求实积分、单位根 |
| 7 | 一阶常系数线性方程 | 32 | 输入—响应框架、叠加原理、余弦输入与辅助角公式 |
| 8 | 二阶线性微分方程 | 36 | 阻尼运动、特征方程三种根情形、Wronskian、存在唯一性、指数输入定理 |
| 9 | 傅里叶级数 | 50 | 共振、正交性与系数公式、周期 2L 与非周期拓展、用级数求特解 |
| 10 | 拉普拉斯（变换） | 62 | 变换律、逆变换解 ODE、卷积、阶跃函数与 δ 函数、传递函数 |
| 11 | 线性齐次微分方程组 | 78 | 特征值/特征向量、重根、复特征根、2×2 相平面作图 |
| 12 | 线性非齐次微分方程组 | 91 | 参数变分法、矩阵指数、方程组解耦、非线性自治系统线性化 |
| 13 | 极限环及方程组关系 | 103 | 极限环定义与存在性（本迪克松准则）、与一阶方程的关系、沃尔泰拉法则 |

> 页码取自编译生成的 `.toc`，前 5 页为封面与目录。

### 知识脉络

```
几何视角(1) ── 数值解(2) ──┐
                           ├─ 一阶方程：线性(3) / 换元(4) / 自治(5)
        复数工具(6) ───────┘
              │
              └─ 二阶线性(7)(8) ── 频域方法：傅里叶(9) / 拉普拉斯(10)
                                        │
                        线性方程组：齐次(11) / 非齐次(12) ── 非线性定性分析(13)
```

## 如何编译

**环境要求**

- 一份完整的 TeX 发行版：**TeX Live 2025**（推荐）或 MiKTeX
- 中文字体：笔记使用 Windows 自带字体（SimSun / SimHei / KaiTi），在 Windows 上开箱即用
- 参考文献需要 `biber`（TeX Live 自带）

**编译引擎**：`pdfLaTeX` 已实测通过（TeX Live 2025，109 页，0 warning）。
由于导言区使用 `ctex`，改用 `XeLaTeX` 也可以，效果更稳。

**推荐做法**

```bash
# 文件名含空格，务必加引号
latexmk -pdf "Notes on Common Calculus Equations.tex"

# 或使用 XeLaTeX
latexmk -xelatex "Notes on Common Calculus Equations.tex"
```

**手工四步（需要参考文献时）**

```bash
pdflatex "Notes on Common Calculus Equations"
biber    "Notes on Common Calculus Equations"
pdflatex "Notes on Common Calculus Equations"
pdflatex "Notes on Common Calculus Equations"
```

> 首次编译务必跑两遍以上，否则交叉引用与目录页码不正确。

## 项目结构

| 文件 / 目录 | 说明 |
|:--|:--|
| `Notes on Common Calculus Equations.tex` | **主文件**：只负责 `\input` 导言区与各章，正文不放在这里 |
| `setup1.tex` | **实际生效的导言区**：宏包、标题作者、章节编号样式 |
| `content.tex` | 目录页（`\newpage` + `\tableofcontents`） |
| `1_geometry.tex` … `13.tex` | 正文 13 章，一章一文件 |
| `mod.tex` | 写作模板（章节/公式/表格/图片骨架），**不参与编译** |
| `references.bib` | 参考文献，目前 1 条（MIT 18.03） |
| `set` / `setup` | 早期导言区副本（历史遗留，未参与编译） |
| `Notes and pictures/` | 全部插图，53 张 PNG，命名对应章节号（如 `cwf10.4.7.png`） |
| `.vscode/` | 编辑器配置；其中 C++ 相关配置与本项目无关 |
| `*.aux` `*.bcf` `*.log` `*.toc` `*.synctex.gz` `*.run.xml` `*.pdf` | 编译产物 |

## 已知问题

1. **⚠️ 插图使用绝对路径（最需要修的一条）**
   54 处 `\includegraphics` 全部写成
   `C:/Users/37/Desktop/Notes on Common Calculus Equations/Notes and pictures/xxx.png`。
   项目现已移动到 `D:\数学\个人笔记库\`，桌面旧目录不存在，**在他处 clone 或在当前位置编译都会报找不到图片**。
   修复方式：把路径前缀批量替换为相对路径 `Notes and pictures/`，例如在项目根目录执行

   ```powershell
   # 在项目根目录执行；用 .NET 写入以避开 PowerShell 5.1 的 UTF-8 BOM 问题
   Get-ChildItem *.tex | ForEach-Object {
     $t = Get-Content $_ -Raw -Encoding UTF8
     $t = $t -replace 'C:/Users/37/Desktop/Notes on Common Calculus Equations/', ''
     [System.IO.File]::WriteAllText($_.FullName, $t, (New-Object System.Text.UTF8Encoding $false))
   }
   ```

   替换后单条引用形如 `\includegraphics[width=0.5\textwidth]{Notes and pictures/cwf10.4.7.png}`。
   可选：在 `setup1.tex` 中再加一行 `\graphicspath{{Notes and pictures/}}` 作为保险。

2. **编译产物被纳入版本管理**：`.aux` `.bcf` `.log` `.toc` `.synctex.gz` 等中间文件已提交，建议加入 `.gitignore`（`.pdf` 可视需要保留，方便读者直接下载）。
3. **导言区存在三份副本**：`set`、`setup`、`setup1.tex` 内容相近且有细微差异（作者署名、是否含 `amsthm`），容易改错文件。建议只保留 `setup1.tex`。
4. **`mod.tex` 模板缺少宏定义**：模板中用了 `\R`、`\Q`、`\z`、`\y`，但项目未定义这些宏，单独编译该模板会报错（正文各章未使用，故不影响主文档）。
5. **字体依赖 Windows**：在 macOS / Linux 上编译需改用 `ctex` 的其它 fontset（如 `fontset=fandol`），或切换到 XeLaTeX 并指定可用中文字体。

## 进度与更新

- **开始时间**：2025 年 12 月 14 日
- **最近编译**：2026 年 5 月 6 日，109 页
- 正文已完成 MIT 18.03 的主干脉络，作者在文末标注「有意思的章节将额外补充」，仍在持续增补。
- 笔记中的「更新时间」由 `\date{\today}` 自动生成，以实际编译日期为准。

## 参考来源

- MIT OpenCourseWare, *MIT 18.03 Differential Equations*, 2006.
- 视频课：<https://www.bilibili.com/video/BV1tx411S77o>
  （见 `references.bib` 中的 `MIT1803` 条目）

## 许可与联系

本项目暂未声明开源许可协议；如需转载、引用或用于课程材料，请先联系作者。

- 记录人：吴奇鑫（源码署名「奇一」）
- 邮箱：<1601430145@qq.com>

---

*笔记难免有疏漏，欢迎通过 Issue 或邮件指出。*
