# 机器增强的人机混合神经系统

吉林大学・车辆工程・复杂系统工程课程小组课题的站点。

本仓库同时承担两件事：**课题门面**（对外说明我们研究什么、在六层体系里处于哪一层）与**过程档案**（每次作业的结论、依据和遗留问题都在这里留痕，可直接交给任课老师查阅）。

## 页面结构（同一链接，三个独立页面）

| 文件 | 对应作业 | 说明 |
| ---- | ---- | ---- |
| `index.html` | 目录入口 | 站点首页：列出作业一、作业二的标题与内容概述，点击卡片跳转到对应作业页面。 |
| `assignment-1.html` | 作业一 | 六层体系梳理与系统解剖：定位、六层要素、三层通路、信号闭环、验证指标、作业归档、进度时间轴。 |
| `assignment-2.html` | 作业二 | BRS / StRS 业务与相关方需求定义，独立成页，不与作业一混排。 |

三个页面互相挂好链接：目录卡片分别指向两个作业页面；两个作业页面顶栏都有「← 目录」返回 `index.html`。部署到 GitHub Pages 后，老师点开目录链接即可看到两次作业，两次作业仍是分开的独立页面。

### 各页面内容

| 页面 | 章节 / 模块 | 内容 |
| ---- | ---- | ---- |
| `assignment-1.html` | 总览 | 定位说明：所选系统处于第四层「系统 Systems」，并解释为什么它不是整机 |
| `assignment-1.html` | 六层梳理 | 任务 → 体系 SoS → 整机 → 系统 → 子系统 → 模块，逐层补全要素，可点选切换 |
| `assignment-1.html` | 系统解剖 | 生物神经层 / 接口层 / 机器算法与执行层三层通路，五个子系统与模块划分表 |
| `assignment-1.html` | 信号闭环 | 上行意图链路与下行反馈链路的闭环图，t₁…t₇ 时延预算分配点 |
| `assignment-1.html` | 验证指标 | 每个指标怎么测、拿什么判定，数值留待实验回填 |
| `assignment-1.html` | 作业提交 | 作业清单、对应章节、提交位置与状态 |
| `assignment-1.html` | 进度 | 从选题到期末汇报的时间节点 |
| `assignment-2.html` | 需求定义 | ConOps / OpsCon 辨析、BRS 八章、StRS 八章、10 类相关方矩阵、3 个运行场景、12 条 Need→Requirement 需求表、质量自检与缩写表 |

三个 HTML 均为自包含文件：CSS、JS、图形全部内联，没有外部依赖（除字体 CDN），双击即可打开。

## 目录结构

```
.
├── index.html         # 目录入口页（作业卡片跳转）
├── assignment-1.html # 作业一：六层体系梳理与系统解剖
├── assignment-2.html # 作业二：BRS / StRS 需求定义
├── README.md         # 本说明
└── docs/              # 每次作业的书面稿与图（可自行创建）
```

## 本地预览

双击 `index.html`。如需通过本地服务器打开（避免个别浏览器对 `file://` 的限制）：

```
python -m http.server 8000
```

然后访问 [http://localhost:8000](http://localhost:8000)。

## 发布到 GitHub Pages

### 方式一：网页上传（不用命令行）

1. 在 GitHub 新建仓库，例如 `hmns-project`，可见性选 Public。
2. 进入仓库 → **Add file → Upload files**，把 `index.html`、`assignment-1.html`、`assignment-2.html` 和 `README.md` 一起拖进去 → Commit。
3. 进入 **Settings → Pages**，`Source` 选 **Deploy from a branch**，分支选 `main`，目录选 `/ (root)`，保存。
4. 等 1–2 分钟，访问 `https://<你的用户名>.github.io/hmns-project/`。

### 方式二：命令行

```
cd hmns-site

git init

git add .

git commit -m "init: 课题站点（目录 + 作业一 + 作业二）"

git branch -M main

git remote add origin https://github.com/<你的用户名>/hmns-project.git

git push -u origin main
```

推上去之后同样在 **Settings → Pages** 里开启 Pages，分支 `main`、目录 `/ (root)`。

> 如果仓库名取作 `<你的用户名>.github.io`，则页面直接发布在 `https://<你的用户名>.github.io/`，不需要子路径。

## 把页面上的仓库按钮接上你自己的仓库

打开 `assignment-1.html`，修改 `<head>` 里这两行（约在第 9–10 行）：

```
<meta name="repo-user" content="">
<meta name="repo-name" content="">
```

填入后，「打开课题仓库」「提交新作业（Issue）」两个按钮就会跳到你自己的仓库；留空时点击会提示去配置，不会跳到错误地址。

## 作业提交流程

1. 新作业单独做一个 `assignment-N.html`，并在 `index.html` 目录页补一张对应卡片。
2. 提交一次 commit，commit message 写 `HW-2: BRS / StRS 需求定义` 这样的格式。
3. 开一条 Issue，标题 `[HW-2] BRS / StRS 需求定义`，正文按模板写三节：

```
## 结论

## 依据

- 引用页面章节：
- 参考材料：

## 遗留问题

-
```

4. 结论变化时更新 Issue 而不是新开一条，让一条记录能完整追溯推导过程。

## 内容约定

* 页面不放未经验证的实验数值。时延、准确率等指标以变量占位（t₁…t₇），实验完成后由小组回填并注明测量条件。
* 引用外部资料时写明来源与获取日期。
* 章节结构与课堂上「任务 — 体系 SoS— 整机 — 系统 — 子系统 — 模块」的链条保持一致，改动前先在组内对齐。
* 每次作业的内容必须显式标注作业次数；作业一已有章节的编号与文案不再改动。
