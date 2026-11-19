[README.md](https://github.com/user-attachments/files/35098716/README.md)
# 协作交付规范 · 精简独立版

发布包：`协作交付规范-精简独立版Skills_v3.0_20261120.zip`；技能标识（slug）：`collab-delivery`；版本 v3.0.0；生成日期 2026-11-20。

## 是什么

一套把单个执行者或多助手团队按“登记—派发—制作—接回—独审—退修—接受—交回”规范协作的可加载技能（Skill）。核心是四约束：真实执行者、同版独审、事件不冒充阶段、核验与接受分离。它不是可自主调度的 Agent，也不是确定性工作流引擎，不自带后台定时器或跨设备恢复。

统一为中性名“协作交付规范”）与**结构精简**（删除 840 个上游源快照文件及历史素材，保留主架构与最实用功能）。

## 来源

精简自公开 MIT 许可的同源技能包 v2.1。原作者版权声明（LICENSE）与第三方声明（NOTICE）依法原样保留——MIT 许可要求副本保留版权与许可文本，删除将违反许可条款，故这两份文件不属于被去除的“产品标识”。除这两份法律文本外，包内不再出现原产品名称、原 slug 或原作者营销性描述。

## 产物清单

| 文件或目录 | 作用 |
|---|---|
| `collab-delivery/SKILL.md` | 唯一加载入口 |
| `collab-delivery/references/*.md` | 10 类认知执行层，按导航渐进加载 |
| `collab-delivery/scripts/*.py` | 4 个可执行契约脚本（严格验收、状态归并、宿主适配、场景门禁） |
| `collab-delivery/contracts/*.json` | 5 份能力 / 验收 / 场景 / 视图 / 策略契约 |
| `collab-delivery/assets/task-and-receipt.md` | 派单、回件、审核、原入口交付模板 |
| `collab-delivery/tests/*.py` | 契约与状态机回归测试（2 组，自洽） |
| `LICENSE` / `NOTICE` | 依法保留的上游版权与第三方声明 |
| `README.md` / `MANIFEST.md` | 说明与结构清单 |

## 复现步骤

解压后将整个 `collab-delivery` 目录交给支持目录式技能的宿主，通过其原生入口加载 `SKILL.md`，保留 references / assets / scripts / contracts。运行回归测试（Python 3.9+，仅标准库）：

```powershell
python -B -m unittest discover -s collab-delivery/tests -v
python -B collab-delivery/scripts/task_state.py --help
```

## 校验结论

- 打包后 24 个文件，无 upstream 快照、无嵌套 zip、无 pdf / mp4 / 大体积素材。
- 全包品牌标识残留检索：0（产品名、原 slug、“一人成队”表述均为 0 命中；LICENSE / NOTICE 的法定版权署名按法律义务保留）。
- 悬空引用检索：0（所有 `references/`、`assets/`、`contracts/`、`scripts/` 链接均指向包内实存文件）。
- 依赖被删 `tools/` 的 `test_release.py` 已剔除；保留的 2 组测试只依赖 `scripts/`，可离线运行。

## 已知边界

- 宿主原生连接器、账号安装与撤回、真实业务评测需外部环境，未测一律标 `untested`，不宣称已通过。
- `policy.example.json` 是合成示例，不构成真实授权；`task_state.py` 只归并状态，不作鉴权。
- 精简版不含上游源快照与历史验证素材，需要逐文件溯源或平台原生打包细节时应另行查证。
