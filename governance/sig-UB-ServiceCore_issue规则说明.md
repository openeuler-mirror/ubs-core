**状态 (Status):** Draft
**作者 (Authors):**  @hlinbo
**创建日期 (Created):** 2026-04-07
**更新日期 (Updated):** 2026-04-07
**相关 Issue/PR:** 

---

# 1. 概述

## 1.1 简介

本文是基于OpenEuler社区issue运行规则的基础上，描述了sig-UB-ServiceCore源码仓的issue规则，指导各项目进行分支操作

## 1.2 动机

OpenEuler社区给出了大量的issue模版，用于方便各sig通过issue完成相应的事务管理

在sig-UB-ServiceCore中没有必要全量使用，所以基于sig-UB-ServiceCore的特征对issue模版进行减少和少量调整

# 2 issue规则定义

## 2.1 用途

通过issue跟踪源码仓的变更过程，源码仓`master分支、openeuler大版本分支`所有的代码合入都要有issue关联（[ubs-core仓](https://atomgit.com/openeuler/ubs-core)除外）

## 2.2 分类

- **Bug：**通过该模版向社区反馈发现的缺陷，并记录缺陷解决过程
- **Feature：**通过该模版向社区反馈或实现新的特性需求，并记录特性的讨论过程及最终的实现和关闭
- **Question：**通过该模版向社区发起求助和提问，通过该模块可以跟踪每个问题的解答和关闭
- **Enhancement：**通过该模版向社区提出改进建议（如代码实现不合理等），并可通过该issue主动向社区提交代码改进

## 2.3 操作规范

### 2.3.1 Bug类issue操作

![img](https://raw.atomgit.com/openeuler/community/files/master/zh/contributors/figure/issue-process-bug.jpg)

step1：新建问题类Issue：**

- 请进入问题所属团队或项目的repository内，进入Issue面板，点击“新建Issue”。
- 如果您不确定该问题对应的团队或项目，请在[community-issue](https://gitcode.com/Ascend/community/issues)中创建，会有社区的开发者帮助进行归属等信息的确认。
- 请在标题栏的单选下拉框将Issue类型设置成“问题”，系统会自动为您调出模板。
- 请在标题栏**简要描述问题的要点**
- 请在详细说明框内按照问题模板的要求描述问题，请参考下面的模板：*请注意：清晰完整的描述有助于团队成员理解，并被更快的接受和排入开发计划。*

```text
【问题描述】
尽可能详细的描述所发生的问题

【环境信息】
请提供昇腾硬件型号与软件环境信息

【重现步骤】
提供尽可能多的信息描述如何重现该缺陷

【预期结果】
描述期望的行为应该是什么样子的

【日志 / 截图】
比如系统message日志/组件日志、dump信息、图片等
```

**step2：审核问题**

- **step2.1**：审核后认可该问题需解决（**进入step3**）
- **step2.2**：审核后认为该问题的信息不全，可以在该Issue的评论区留言或在邮件列表中讨论，让提交人继续补充相关信息。
  - **step2.2.1**：如果在一个月内提交人未及时补充相关信息，则系统会自动关闭该问题（**跳到step8.3**）
  - **step2.2.2**：Issue提交人补充信息后，可以通过评论让团队成员继续审核（**跳到step2**）
- **step2.3**：审核后确认是问题，但由于各种原因暂时不解决挂起（**跳到step8.7**）。这种情况通常包括：
  - 情况一：该问题是一个bug，它将在下一个受支持的发行版中修复，但不计划在针对该错误提交的发行版本中解决。这种情况最好复制一个Issue到下一个版本
  - 情况二：Maintainer希望最终由上游开发修复并更新过程中解决该问题。此种情况请添加注释并附上上游社区此问题的错误报告链接
- **step2.4**：审核后发现问题是重复的，附上重复问题的链接（**跳到step8.4**）
- **step2.5**：审核后认为是非问题，说明认为是非问题的原因（**跳到step8.6**）
  - 情况一：现象是正常的，不是问题
  - 情况二：该问题所在的版本已经不再维护，且后继的版本没有该问题
- **step2.6**：审核后认为是确实存在问题，但不进行解决（**跳到step8.5**）
  - 情况一：问题解决代价大但影响很小，所以解决价值不大，不解决。
  - 情况二：是问题，但不是当前组件的问题

**step3：认领或分配问题**。可以主动认领，也可以由团队成员分配。您可以在评论框内输入`/assign`来把Issue分配给自己，或分配给其他人。

**step4：完成修改并提交PR**。完成修改和本地验证后，在提交PR的时候需附上本Issue的链接，请参考Gitcode的相关帮助文档：[Pull Request关联Issue](https://docs.gitcode.com/docs/help/home/org_project/pullrequests/pr-related-issue)。提交PR的具体的方法请参考[提交PR指导](pr-guide.md)内容。

**step5：项目内验证**。项目内对修改的PR进行验证。如果验证不通过（**回到step4**）。如果验证通过，同时该问题不是版本的问题，此问题以**项目组问题关闭**。

**step6：提交或发布patch**。项目组的Maintainer决定该问题的解决方式，可以是更新软件包或发布patch。如果该问题属于版本类关键问题，需要QA团队验证。

**step7：QA组验证**：QA组会对此类问题从版本层面进行验证。验证通过后，

**step8：问题关闭**：问题关闭有以下几种类型，那哪种类型关闭问题，请在描述框中说明：

- step8.1：项目内问题解决关闭
- step8.2：版本问题解决关闭
- step8.3：问题信息长期得不到解决关闭
- step8.4：重复问题关闭
- step8.5：问题不解决关闭
- step8.6：非问题关闭
- step8.7：问题暂不解决挂起

### 2.3.2 Feature类issue操作

![img](https://raw.atomgit.com/openeuler/community/files/master/zh/contributors/figure/issue-process-requirement.jpg)

**step1：新建需求类Issue**（Issue状态：待办的）

- 请进入需求对应的团队或项目的repository内（如何找到对应的repository请参考[此章节内容](https://atomgit.com/openeuler/community/tree/master/zh/contributors/README.md/#id2-1-2)），进入Issue面板，点击“新建Issue”。
- 如果您不确定该需求对应的团队或项目，请在[community-issue](https://link.atomgit.com/?target=https%3A%2F%2Fgitee.com%2Fopeneuler%2Fcommunity-issue&from=https%3A%2F%2Fatomgit.com%2Fopeneuler%2Fcommunity%2Fblob%2Fmaster%2Fzh%2Fcontributors%2Fissue-submit.md&lang=zh&theme=white)中创建，会有社区的开发者帮助进行归属等信息的确认。
- 请在标题栏的单选下拉框将Issue类型设置成“需求”，系统会自动为您调出需求模板
- 请在标题栏**简要描述需求的要点**
- 请在详细说明框内说明需求的场景和价值。

*请注意：清晰完整的描述有助于团队成员理解，并被更快的接受和排入开发计划。*

**step2：团队成员审核Issue**（Issue状态——通过：进行中 *或者* 补充信息： 待办的 *或者* 拒绝：已拒绝 ）

- **step2.1**：审核后接纳

  团队成员（maintainer或者committer）审核后认为可以接纳该需求，则由审核人补充接纳需求的相关信息，并包含：

  - 检查并设置该需求所属的项目
  - 设置该需求建议合入的里程碑信息（规划版本信息）
  - 设置该需求的优先级标签，请在标签栏选择“feature:High”、“feature:Medium”或者"feature:Low"
  - 完成以上的信息以后，请将该Issue的“当前状态”调整成“进行中”（**进入step3**）

- **step2.2**：描述不清晰挂起

  团队成员审核后认为描述的信息不清晰，可以在该Issue的评论区留言或在邮件列表中讨论，让提交人继续补充相关信息。

- **step2.2.1**：如果在一个月内提交人未及时补充相关信息，则系统会自动关闭该问题（**跳到step4**）

  - **step2.2.2**：Issue提交人补充信息后，可以通过评论让团队成员审核（**跳到step2**）。

  **step2.3**：审核后不接纳

  团队成员审核后，由于需求价值不高等原因认为暂不接纳，可以在评论区留言或在邮件列表中讨论说明原因。确认后将Issue的“当前状态”调整成“已拒绝”（**跳到step4**）

**step3：认领或分派Issue**（Issue状态：开启的）

已经进入开发阶段的需求，可以主动认领，也可以由团队成员分配。您可以在评论框内输入`/assign`来把Issue分配给自己，或分配给其他人。

**step4：关闭Issue**，关闭Issue有三种情况：

- 需求完成后关闭，可以由认领人手工修改状态，也可以通过关联PR后，由PR审核通过后系统自动关闭。
- 需求被拒接关闭，由审核人手工修改状态
- 需求超期后关闭，由系统自动根据需求停滞的时间进行超期关闭的操作

### 2.3.3 Question类issue操作

同Feature类issue

### 2.3.4 Enhancement类issue操作

同Feature类issue