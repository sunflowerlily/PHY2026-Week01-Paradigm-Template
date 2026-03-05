# Week 1 Assignment: The Paradigm Shift & The Error Trap

## 🎯 实验目标
1.  **环境验证**: 确保你的 Python (Numpy, Matplotlib) 和 Git 环境配置正确。
2.  **物理洞察**: 理解数值计算中**截断误差 (Truncation Error)** 与 **舍入误差 (Round-off Error)** 的博弈。
3.  **AI 协同**: 体验 "Blindly trusting AI" (盲信 AI) 与 "Guiding AI with Physics" (物理引导 AI) 的区别。

## 👥 参与方式 (GitHub Classroom 操作指南)
本实验在 GitHub Classroom 上设置为 **Group Assignment**（小组作业）。
**考虑到班级规模 (53人)，建议组成 10-12 个小组，每组 4-5 人。**

### 建组规则 (Team Setup)
1.  **队长 (Team Leader)**：
    *   点击邀请链接 -> 选择 "Create a new team"。
    *   **Team Name**: `Group-XX` (例如 `Group-01`, `Group-12`)。
    *   创建后，将组名告知队友。
2.  **队员 (Members)**：
    *   点击邀请链接 -> **不要创建新队**。
    *   在列表中找到队长的 `Group-XX`，点击 **Join**。

| 模式 | 人数 | 预估耗时 | 说明 |
|:---|:---|:---|:---|
| **标准小组** | **4-5人** | **1 小时** | 分工明确，流水线作业，适合高效完成任务。 |
| **硬核单人** | 1人 | 3 小时 | 仅限想要挑战全栈能力的同学 (需向老师报备)。 |

### 🛠️ 角色分工建议 (Roles)
为了防止“搭便车”，请明确认领以下角色（可在报告中署名）：

*   **Member A (Core Dev)**: 负责 `lab1_core`，实现核心差分算法。
*   **Member B (Algo Dev)**: 负责 `lab2_bonus`，攻克 Richardson 外推法。
*   **Member C (Data Vis)**: 负责 `notebook_error.ipynb`，将 A 和 B 的数据可视化对比。
*   **Member D (QA Engineer)**: **质量保证**。负责运行 `pytest`，检查代码规范 (PEP8)，确保无低级错误。
*   **Member E (Physics Lead)**: **物理分析**。主笔实验报告，深度解释“V字形误差曲线”背后的物理机制。

*(若小组只有 4 人，可由 Member D 兼任 Report 工作)*

## 📂 目录结构
```tree
.
├── README.md               # [To Student] 实验指导书
├── Report_Template.md      # [Team] 最终实验报告模板
├── requirements.txt        # 依赖包列表
├── notebook_error.ipynb    # [Member C] 数据汇总与可视化笔记本
├── lab1_core/              # [Member A] 核心任务
│   ├── src/
│   │   ├── ai_bad_code.py      # [Part A] AI 陷阱分析
│   │   └── differentiation.py  # [Part B] 核心代码模板
│   └── tests/
│       └── test_core.py        # [Member D] 自动评分脚本
└── lab2_bonus/             # [Member B] 进阶任务
    └── src/
        └── richardson.py       # [Part C] 高阶精度算法模板
```

## 🚀 任务指南

### Part A: AI 的物理陷阱 (The Trap)
1.  进入 `lab1_core/src/` 目录。
2.  运行 `python ai_bad_code.py`。
3.  你会发现程序输出了一个警告，或者计算出的导数误差巨大。
4.  **思考**: 为什么 AI 选择极小的步长 ($h=10^{-15}$) 却得到了错误的结果？
    *   *提示*: 回忆课堂上讲的浮点数精度 ($\epsilon \approx 10^{-16}$)。
    *   在 `ai_bad_code.py` 的注释中简要写下你的分析。

### Part B: 核心重构 (Core)
1.  打开 `lab1_core/src/differentiation.py`。
2.  这是一个未完成的模板。你需要实现 `central_difference` 函数，并完成 `analyze_error` 函数中的绘图逻辑。
3.  **核心任务**:
    *   实现中心差分公式: $f'(x) \approx \frac{f(x+h) - f(x-h)}{2h}$
    *   扫描步长 $h$ 从 $10^{-16}$ 到 $10^{0}$。
    *   绘制双对数坐标图 (log-log plot): 横轴为 $h$，纵轴为相对误差。
    *   找出误差最小的 **最优步长 (Optimal Step Size)**。

### Part C: 进阶挑战 (Bonus)
1.  打开 `lab2_bonus/src/richardson.py`。
2.  研究 Richardson 外推法原理（或询问 AI："Explain Richardson extrapolation for numerical differentiation"）。
3.  实现 $D_{richardson}(h) = \frac{4 D(h/2) - D(h)}{3}$。
4.  验证其误差是否真的比普通中心差分更小。尝试用大步长（如 $h=0.1$）获得高精度。

### Part D: 验证与提交
1.  **QA 环节 (Member D)**: 运行测试脚本检查代码是否正确:
    ```bash
    pytest lab1_core/tests/test_core.py
    ```
2.  **整合报告 (Member C & E)**: 运行 `notebook_error.ipynb`，对比两种算法的精度，并将结果填入 `Report_Template.md`。
3.  提交代码到 GitHub:
    ```bash
    git add .
    git commit -m "feat: completed week 1 assignment"
    git push
    ```

## 📝 评分标准
| 检查项 | 权重 | 说明 |
|:---|:---:|:---|
| **GitHub Actions** | 50% | `test_core.py` 全部通过 |
| **Bonus Task** | 20% | `richardson.py` 实现正确，并有对比分析 |
| **Report Quality** | 30% | `Report_Template.md` 填写完整，物理分析深入 |

---
> **教师寄语**: 计算物理不再是死记硬背公式，而是要学会如何用计算机去验证物理直觉。AI 是你的副驾驶，但方向盘始终在你手里。
