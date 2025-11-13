<h1><p style="text-align: center" type="">
    sig-UB-ServiceCore release & API Governance
    </p></h1>

[TOC]

| Revision | Data     | Revision Description | Author         |
| -------- | -------- | -------------------- | -------------- |
| v1.0     | 2025/8/6 | 评审通过，发布v1.0   | 高维涛，姚弋宇 |

> 文档决策路径:
>
> - 社区文档发布建议决策路径：PC会签->发布内源社区（版本号迭代）->开源社区SIG决策->开源社区发布
>
> - 内部文档发布建议决策路径：PC会签->发布内源社区

# 1 OpenEuler社区版本管理规范

| 社区      | 包/SDK版本管理规范                                           | API版本规范              |
| --------- | ------------------------------------------------------------ | ------------------------ |
| openEuler | [RPM](https://gitee.com/openeuler/community/blob/master/zh/contributors/packaging.md)包：<br />1、命名方式：组件名-包类型(主包，libs，devel，static包，help包)-major.minor.patch.{arch}.rpm<br />2、源码包：组件名-版本.tar.gz<br />3、版本兼容性管理：遵循LSB | 项目自行运作，无明确规范 |

# 2 sig-UB-ServiceCore 交付件/API/发布管理规范

## 2.1 sig-UB-ServiceCore社区交付件管理规范

> **约束：** 为提升最终用户易用性，RPM报名与仓库名需相同

| 交付件类型 | 规范                                                         |
| ---------- | ------------------------------------------------------------ |
| RPM版本    | 遵循[openEuler社区规范](https://gitee.com/openeuler/community/blob/master/zh/contributors/packaging.md)，以**Major.minor.patch**管理版本 |
| RPM命名    | modulename-{type}-{ver}-{arch}.rpm  type= libs,devel,static,help |
| so命名     | libxxx_xxx.so  //lib 开头，如需分割，以下划线_分割           |
| ko命名     | 名称按需命名，如需分割，以下划线分割                         |
| 代码仓     | ubs-modulename                                               |
| 实例化参考 | 以UBS Engine为例：<br />RPM包：<br />ubs-engine-1.0.0-.aarch64.rpm<br/>ubs-engine-client-libs-1.0.0.aarch64.rpm<br/>ubs-engine-client-devel-1.0.0.aarch64.rpm<br />so<br />libubse_client.so<br />仓名<br />openEuler/ubs-engine |

## 2.2 sig-UB-ServiceCore社区API 管理规范

> API规范建议原则：
>
> - 降低管理成本
> - 规范API运作，API开发全流程透明

| API管理     | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| API规范定义 | 1、API不单独管理，随release发布<br />2、API成熟度定义为alpha，beta，GA/Release，通过API文档承载具体到每个接口管理<br />**alpha定义**：无二进制，仅作为初期讨论，不承诺兼容型<br />**beta定义**：有配套临时二进制版本，有基础的接口兼容保证，变更通过社区协作方式同步<br />**GA/Release定义**：有配套的GA二进制版本，API接口冻结，原则上要求全部前向兼容<br /> |

## 2.3 sig-UB-ServiceCore社区镜像发布规范

### 2.3.1 openEuler Base/Everything版本

| **版本类型**                                                 | **定义**                                                     | **包含内容**                                                 | **要求**             | **申请方式**                                               | UBSCore实例化                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------- | ---------------------------------------------------------- | ------------------------------------------------------------ |
| [base](https://repo.openeuler.org/openEuler-22.03-LTS-SP2/OS/x86_64/) | 放到 repo仓下面的OS目录的即为Base内容，会放到标准ISO里面，能加到开机默认安装列表 | 系统基础组件：bash, coreutils, systemd, glibc, kernel  网络与服务：NetworkManager，openssh，firewalld，bind，ModemManager  安全与认证：audit，authselect，aide  开发者工具：gcc，make，cmake，boost，SDL，ImageMagick，binutils，bison，autoconf  图形与桌面：gtk，qt，xorg，adwaita-icon-theme, cantarell-fonts  包管理：dnf，yum，packagekit，rpm  EFI/ks/docs/公钥/isolinux引导文件/包元数据/安装镜像文件/文档等 | 一般需要保证前向兼容 | 首次在TC申请创建创建仓库即要规划好在Base仓还是Everything仓 | 1、在TC申请UBS Core SIG，同时申请对应仓目录  2、UBS Core各组件申请放入base仓  3、rpm包平铺于package仓下 |
| everything                                                   | 全量rpm包                                                    | /                                                            | 社区统一要求         | /                                                          | 申请SIG同时创建仓库即可                                      |

### 2.3.2 sig-UB-ServiceCore 发布规范

| 发布件       | 发布形态                                                     | 发布位置         | 安装方式                                                     |
| ------------ | ------------------------------------------------------------ | ---------------- | ------------------------------------------------------------ |
| UBS Core     | 1、跟随openEuler版本，如2203.<br />2、代码仓为空仓，通过spec来下载其他代码安装 | base             | 1、开放配置文件，通过Spec定义默认启动服务，其他服务按需启动<br />2、场景化部署通过文档支撑 |
| UBS Core组件 | major.minor.patch                                            | base(待明确大小) | spec中自行定义静态依赖与运行依赖                             |



