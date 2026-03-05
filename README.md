# Week 1 Assignment: The Paradigm Shift & The Error Trap

## 🎯 实验目标
1.  **环境验证**: 确保你的 Python (Numpy, Matplotlib) 和 Git 环境配置正确。
2.  **物理洞察**: 理解数值计算中**截断误差 (Truncation Error)** 与 **舍入误差 (Round-off Error)** 的博弈。
3.  **AI 协同**: 体验 "Blindly trusting AI" (盲信 AI) 与 "Guiding AI with Physics" (物理引导 AI) 的区别。

## 👥 参与方式 (GitHub Classroom 操作指南)
本实验在 GitHub Classroom 上设置为 **Group Assignment**（小组作业），但也完全支持单人挑战。**请在点击邀请链接后仔细操作**：

### 1. 想要【单人挑战】的同学 (Solo Mode)
*   点击邀请链接后，GitHub 会问你 "Join an existing team" 还是 "Create a new team"。
*   **请选择 "Create a new team"**。
*   **Team Name 命名规则**: `Solo-学号-姓名拼音` (例如: `Solo-2024001-ZhangSan`)。
*   创建后，你将独自拥有一个仓库，独自完成所有 Part A, B, C。

### 2. 想要【小组协作】的同学 (Team Mode)
*   **第一个人 (队长)**：
    *   点击邀请链接 -> 选择 "Create a new team"。
    *   **Team Name 命名规则**: `Team-队名` (例如: `Team-Alpha`)。
    *   创建后，把你的队名告诉队友。
*   **第二/三个人 (队员)**：
    *   点击邀请链接 -> **不要创建新队**。
    *   在列表中找到队长的 `Team-Alpha`，点击 **Join**。
*   **注意**: 
    *   一旦加入队伍，通常无法自行退出，请谨慎操作。
    *   所有组员共享同一个仓库，请多使用 `git pull` 避免冲突。

| 模式 | 推荐人群 | 预估耗时 | 分工建议 |
|:---|:---|:---|:---|
| **单人模式** | 编程基础较好，挑战全栈 | **2-3h** | 独立完成所有模块。 |
| **小组模式** | 编程新手，合作学习 | **1-1.5h** | Member A: Core; Member B: Bonus; Member C: Report. |

## 📂 目录结构
```tree
.
├── README.md               # [To Student] 实验指导书
├── Report_Template.md      # [Team/Solo] 最终实验报告模板
├── requirements.txt        # 依赖包列表
├── notebook_error.ipynb    # [Visualization] 数据汇总与可视化笔记本
├── lab1_core/              # [Core Task] 核心任务
│   ├── src/
│   │   ├── ai_bad_code.py      # [Part A] 一个充满陷阱的 AI 生成代码
│   │   └── differentiation.py  # [Part B] 核心代码模板
│   └── tests/
│       └── test_core.py        # 自动评分脚本
└── lab2_bonus/             # [Bonus Task] 进阶任务
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
1.  运行测试脚本检查代码是否正确:
    ```bash
    pytest lab1_core/tests/test_core.py
    ```
2.  **整合报告**: 运行 `notebook_error.ipynb`，对比两种算法的精度，并将结果填入 `Report_Template.md`。
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
