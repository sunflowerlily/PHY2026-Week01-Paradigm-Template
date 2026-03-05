# 实验报告：The Paradigm Shift

**小组 ID**: [例如 Group-01]

**成员名单与分工**:
*   Member A (Core Dev): 姓名 (学号) - GitHub ID
*   Member B (Algo Dev): 姓名 (学号) - GitHub ID
*   Member C (Data Vis): 姓名 (学号) - GitHub ID
*   Member D (QA Lead):  姓名 (学号) - GitHub ID
*   Member E (Physics):  姓名 (学号) - GitHub ID

*(注：请务必填写真实分工，这将作为个人贡献度评估的依据)*

---

## 🎯 Lab 1: 核心排雷记录

### 1. AI 毒药代码分析 (Task A)
*   **现象描述**：当步长 $h < 10^{-16}$ 时，输出变成了什么？
    *   [在此处填写]
*   **物理原因**：
    *   [解释 Catastrophic Cancellation]
*   **修复方案**：
    *   [粘贴修复后的关键代码片段]

### 2. V 字形误差曲线 (Task B & C)
*   **最佳步长 (Sweet Spot)**：$h \approx$ [填写数值]
*   **曲线分析 (由 Physics Lead 主笔)**：
    *   左侧上升是因为：[填写原因]
    *   右侧下降是因为：[填写原因]
*   **插入截图**：
    *   ![Error Plot](在此处插入 notebook 生成的图片)

### 3. AI 交互记录 (Prompt Engineering)
*   **我们使用的 Prompt**：
    ```text
    [在此粘贴你们引导 AI 修复代码或解释误差的 Prompt]
    ```
*   **AI 的反馈质量评分 (1-5星)**：⭐⭐⭐

---

## 🚀 Lab 2: 进阶挑战 (理查德森外推)

*   **收敛速度对比**：
    *   普通差分法的斜率 (Log-Log图) $\approx$ [填写]
    *   理查德森外推法的斜率 $\approx$ [填写]
*   **结论**：[一句话总结高阶算法的优势]

---

## 🛠️ QA 报告 (由 QA Engineer 填写)
*   [ ] 所有 Python 文件是否符合 PEP8 规范？
*   [ ] `pytest` 是否全部通过？
*   [ ] 是否已检查过没有将 `__pycache__` 或 `.DS_Store` 上传到 GitHub？
