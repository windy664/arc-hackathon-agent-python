<div align="center">

<img src="assets/banner.svg" alt="arc-hackathon-agent-python" width="100%">

# arc-hackathon-agent-python

**ARC-Bench 编程智能体（Python 实现）** —— 需求分解、多智能体协作与视觉验收，在有限 Token 预算内完成开发任务。

![Python](https://img.shields.io/badge/Python-3.x-3776ab?style=flat-square&logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Bench-ARC--Bench-8b5cf6?style=flat-square)
![Tests](https://img.shields.io/badge/pytest-ready-3da639?style=flat-square&logo=pytest&logoColor=white)

[用法](#-用法) · [结构](#-结构)

</div>

## 🚀 用法

平台入口约定为根目录 `main.py`：

```bash
python3 main.py /path/to/requirements --output-dir /path/to/output [--type web]
```

- 源目录缺省取环境变量 `ARCBENCH_TASK_DIR`（默认 `./requirements`）
- 输出目录缺省取 `ARCBENCH_OUTPUT_DIR` / `ARCBENCH_TEMPLATE_DIR`（默认 `/workspace/template`）
- `--type web` 指定应用类型（`app_type_handler` 负责归一化，`app_type_handler.list_app_types` 可枚举）

本地独立入口 `arc_main.py` 提供更完整的 CLI（调试日志、异步流水线）。

## 🧱 结构

| 路径 | 职责 |
|------|------|
| `compiler/` | 核心流水线：需求解析 → 规划 → 生成 → 校验 |
| `agents/` | 多智能体实现 |
| `skills/` | 注入给智能体的技能包 |
| `core/` | CLI、日志、公共工具 |
| `app_type_handler/` | 应用类型识别与归一化 |
| `arcbench_agent_runtime/` | 平台运行时适配 |
| `monitor.py` | 运行监控 |
| `forensics.py` | 失败现场取证 |
| `tests/` | pytest 测试（`pytest.ini`） |

实验记录见 [EXPERIMENTS.md](EXPERIMENTS.md) 与 [REPAIR.md](REPAIR.md)。

## 🔧 开发

```bash
pip install -r requirements.txt
pytest
```

> 同系列（TypeScript 实现）：[Torine-hackathon-agent-ts](https://github.com/windy664/Torine-hackathon-agent-ts)
