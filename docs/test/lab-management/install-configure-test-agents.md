---
title: "安装和配置测试代理 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: fdcca04c9dd06132496912f4df30e3d86d24d42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="install-and-configure-test-agents"></a>安装和配置测试代理

对于使用 Visual Studio 和 Visual Studio Team Services 或 Team Foundation Server (TFS) 的测试方案，不需要使用测试控制器，因为 Agents for Microsoft Visual Studio 会通过与 Team Services 或 TFS 进行通信来处理业务流程。 例如，使用 Team Services 或 TFS 中的生成和发布工作流运行持续测试。

如果需要将测试代理或测试控制器和 TFS 2013 配合使用，请使用 Agents for Microsoft Visual Studio 2013 Update 5 并配置测试控制器。

还可考虑[改为使用 Build Management 或 Release Management ](use-build-or-rm-instead-of-lab-management.md)是否会更简单。

## <a name="what-do-i-need"></a>需要什么？

**从哪里获取测试控制器和测试代理？**

* 如果正在使用“生成 vNext”任务运行测试，并且想从本地目录安装代理 - 

  * [下载 Agents for Microsoft Visual Studio 2015 RTM 和 Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266)。 

  * [下载 Agents for Microsoft Visual Studio 2017 和 Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs) - 在左侧导航栏中选择“用于 Visual Studio 2015 的工具”，然后选择“Agents for Visual Studio 2015”。

* 如果想运行以下内容，请[下载 Agents for Microsoft Visual Studio 2013 Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264)：

  * 使用本地远程计算机运行负载测试。

  * 使用 Microsoft 测试管理器或 MSTest 运行远程持续测试以及对实验室环境进行测试设置。

  * 使用 TFS 2013 运行持续测试。

这些安装程序可用作 ISO 文件（虚拟 CD），便于在虚拟机上安装。 

[是否可以混合使用各种版本的 TFS、Microsoft 测试管理器、测试控制器和测试代理？](#MixedVersions)

**安装测试控制器和测试代理有什么系统要求？**

| 项 | 要求 |
| ---- | ------------ |
| **代理** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2，Service Pack 1 |
| **控制器** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2，Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>问题解答

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>问：是否可以混合使用各种版本的 TFS、Microsoft 测试管理器、测试控制器和测试代理？

答：可以，兼容和支持的组合如下：

| TFS | 带实验中心的 Microsoft 测试管理器 | 控制器 | 代理 |
| --- | -------------------------------------- | ---------- | ----- |
| 2015：从 2013 升级 | 2013 | 2013 |2013 |
| 2015：全新安装 | 2013 | 2013 | 2013 |
| 2015：从 2013 升级或全新安装 | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>问：Test Agent 2015 是否支持 Test Controller 和 Test Agent of Visual Studio 2013 支持的所有方案？

A：建议在所有新的自动测试方案中都使用 Agents for Visual Studio。 可以在生成定义中使用“部署测试代理”任务在计算机上下载和安装测试代理。
下表显示了 Agents for Visual Studio 2013 支持的方案，以及 Team Foundation Server (TFS) 2015 和 Team Services (TS) 的替代方案。

| Agents for Visual Studio 2013 支持的方案 | TFS 和 TS 中的替代方案 |
| --- | --- |
| Visual Studio 中的“生成-部署-测试工”作流 | 用户可以在 TFS 中使用[生成定义](https://www.visualstudio.com/team-services/continuous-integration/)（而不是 XAML 生成）生成、部署和测试方案。 |
| 使用本地远程计算机进行负载测试（性能测试） | 使用 Test Controller/Test Agents 2013 Update 5 在本地运行负载测试。 [详细信息](https://msdn.microsoft.com/en-us/library/ff400223.aspx)。 |
| 使用实验室环境从 Microsoft 测试管理器远程执行自动测试 | 目前此方案没有替代方案。 建议在生成和发布定义（而不是 XAML 生成）中使用“运行功能测试”任务来远程执行测试。 |
| 开发人员在 Visual Studio 中执行远程测试 | 不再支持。 |

<!-- ENDSECTION -->

## <a name="see-also"></a>另请参阅

* [使用测试设置来设置计算机和收集诊断信息](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
