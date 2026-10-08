# AGENTS.md

## 统一时间戳规则（所有项目 / 最高优先级）

- ChatGPT、OpenCode、PI 的每一条用户可见回复、状态回执、TASK/REPORT/STATE 交接说明，第一行必须写：`YYYY-MM-DD HH:MM｜执行器：ChatGPT / OpenCode / PI｜当前阶段：<阶段>`。
- 时间必须是实际当轮中国时间 Asia/Shanghai（UTC+8），精确到分钟。OpenCode/PI 本地运行开始前和结束回执前都必须重新取得实际时间，不得沿用旧任务时间或机器本地时区猜测。
- 无法核实时写“时间未核实”，不得编造。`TASK_ID` 不能代替时间戳；即使只输出 `TASK_READY`、`DONE`、`BLOCKED`、`跑完了`，也必须带时间戳。
- 每轮末尾固定写：`完成时间`、`当前阶段`、`当前状态`、`下一步`、`你现在要做`。

## 默认协作规则

- ChatGPT 负责设计、代码、任务和审核。
- OpenCode 负责按任务执行并如实报告，不自行改变业务逻辑。
- PI 只执行 ChatGPT 明确下发的检索和核验任务。
- 开始前先安全 `git pull --ff-only`，再读取本文件和当前 TASK/STATE。

完成时间：YYYY-MM-DD HH:MM（中国时间）
当前阶段：<阶段>
当前状态：DONE / BLOCKED / PENDING
下一步：ChatGPT / OpenCode / PI / 用户
你现在要做：具体操作
