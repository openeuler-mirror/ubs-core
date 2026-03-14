**状态 (Status):** Approved

**作者 (Authors):** @luwei @hlinbo

**创建日期 (Created):** 2026-03-13

**更新日期 (Updated):** 2026-03-13

**相关 Issue/PR:** 

---

# 1. 概述

## 1.1 简介

对ubs-engine、ubs-virt两个项目进行调整

## 1.2 动机

基于sig运作的要求，方面各项目角色的履职，审视各项目committer的情况

## 1.3 目标

明确项目角色

# 2 调整项目及内容

## 2.1 ubs-engine新增committer

```yaml
 - repo:
   - openeuler/ubs-engine	 
   - src-openeuler/ubs-engine	 
   committers:
   ...
   - gitee_id: HJLi96
     atomgit_id: HJLi96
     name: Hongjie Li
     organization: Huawei
     email: lihongjie17@huawei.com
```



## 2.2 ubs-virt调整committer

```yaml
 - repo:	 
   - openeuler/ubs-virt	 
   - src-openeuler/ubs-virt	 
   committers:
   - gitee_id: areigonglei  # 保留
     atomgit_id: areigonglei
     name: Lei Gong
     organization: Huawei
     email: arei.gonglei@huawei.com
   - gitee_id: chenxiaoyu93  # 移除
     atomgit_id: chenxiaoyu93
     name: Xiaoyu Chen
     organization: Huawei
     email: chenxiaoyu48@huawei.com
   - gitee_id: Sky_miner  # 移除
     atomgit_id: Sky_miner
     name: Yichen Liu
     organization: Huawei
     email: liuyichen23@huawei.com
   - gitee_id: wuzw_05  # 移除
     atomgit_id: wuzw_05
     name: Zhiwei Wu
     organization: Huawei
     email: wuzhiwei37@huawei.com
   - gitee_id: julyfish  # 移除
     atomgit_id: julyfish
     name: Luyue Ji
     organization: Huawei
     email: jiluyue@huawei.com
   - gitee_id: NotCold    # 新增
     atomgit_id: NotCold
     name: Han Mo
     organization: Huawei
     email: mohan5@huawei.com
   - gitee_id: yutao88    # 新增
     atomgit_id: yutao88
     name: Tao Yu
     organization: Huawei
     email: yutao88@huawei.com
   - gitee_id: HJLi96    # 新增
     atomgit_id: HJLi96
     name: Hongjie Li
     organization: Huawei
     email: lihongjie17@huawei.com
```

