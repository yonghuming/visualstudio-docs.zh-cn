---
title: "使用实验室环境进行开发 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lab environment, test lab
ms.assetid: b435eb39-dc7c-46fa-a91b-6e6dd614f01c
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 29b1343159cb91d3d5e4b9769c4103cc3565f986
ms.contentlocale: zh-cn
ms.lasthandoff: 06/02/2017

---
# <a name="use-a-lab-environment-for-your-devops"></a>使用实验室环境进行开发

实验室环境是可用于开发和测试应用程序的虚拟和物理计算机的集合。 实验室环境可包含测试多层应用程序所需的多个角色，如工作站、Web 服务器和数据库服务器。 此外，还可以在实验室环境下使用生成-部署-测试工作流，以实现在应用程序上生成、部署和运行自动测试的过程的自动化。

* **使用测试计划运行自动化测试** - 可以运行自动化测试的集合（称为测试计划），并查看进度。  
  
* **使用“生成-部署-测试”工作流** - 可以使用“生成-部署-测试”工作流自动测试多层应用程序。 一个典型示例是在实验室环境中启动生成、在实验室环境中将生成文件部署到适当的计算机然后执行自动化测试的工作流。 此外，你还可以将你的工作流规划为按照指定间隔运行。  
  
* **从所有计算机收集诊断数据（即使在手动测试期间）**- 可以同时从多台计算机收集诊断数据。 例如，在单个测试运行期间，你可以从 Web 服务器、数据服务器和客户端收集 IntelliTrace、测试影响和其他形式的数据。  
  
以下是实验室环境的常用类型的示例：  
  
| 拓扑 | 描述 |  
|---|---|  
|![仅包含服务器的拓扑](../media/topology_backend.png)| 此实验室环境具有服务器拓扑，此拓扑常用于在服务器应用程序上运行手动测试，并且允许测试人员使用他们自己的客户端计算机验证环境中的 bug。 在后端拓扑中，你的实验室环境仅包含服务器。 当你使用此类型的拓扑时，通常使用不属于该环境一部分的客户端计算机连接实验室环境中的服务器。|  
|![云实验室环境](../media/topology_cloud.png)| 此实验室环境提供的功能与服务器拓扑类似，但无需在本地环境运行物理计算机或虚拟机，这样可以缩短安装时间、简化维护过程并降低成本。 在 Microsoft Azure 等云环境中可以快速方便地设置多个网站、虚拟机和自定义网络。 [更多详细信息](#usebandrm)。|  
|![客户端服务器实验室环境](../media/topology_clientserver.png)| 此实验室环境具有客户端-服务器拓扑，此拓扑常用于测试具有服务器和客户端组件的应用程序。 在客户端/服务器拓扑中，所有用于测试应用程序的所有客户端和服务器计算机都在你的实验室环境中。 当你使用此拓扑时，你可以从影响测试的每台计算机收集测试数据。|  
  
请参阅[视频：管理用于测试的实验室环境](http://go.microsoft.com/fwlink/?LinkID=252614)。  
  
设置实验室环境的典型方法包括： 
  
* [通过 Team Services 或 Team Foundation Server 生成和发布使用云](#usebandrm)

* [使用 Microsoft 测试管理器的 Visual Studio 实验室管理工具版功能](#usemtmlm)

<a name="usebandrm"></a>
## <a name="use-the-cloud-with-team-services-or-team-foundation-server-build-amp-release"></a>通过 Team Services 或 Team Foundation Server 生成和发布使用云

使用 Team Foundation Server (TFS) 和 Visual Studio Team Services 中的[生成和发布](https://www.visualstudio.com/team-services/continuous-integration/)功能可以执行自动测试和生成-部署-测试自动化。 部分优势包括：

* 不需要生成控制器或测试控制器。
* 生成或发布过程中会通过任务安装测试代理。
* 可以轻松地自定义部署步骤。 不再受到使用单一脚本的限制。 还可利用产品和 Visual Studio Marketplace 中提供的许多任务。
* 无需维护测试套件。 可从二进制文件直接运行测试。
* 每个生成或发布中运行的测试会提供更丰富的内联报告体验。
* 可以跟踪每个环境上当前部署和测试的资产类型（发布、生成、工作项、提交）。
* 可自定义和扩展自动化，并轻松部署到多个测试环境，甚至生产环境。
* 可计划在签入或提交时，或在每天的特定时间执行自动化操作。

[详细信息](use-build-or-rm-instead-of-lab-management.md)。

<a name="usemtmlm"></a>
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>使用 Microsoft 测试管理器的 Visual Studio 实验室管理工具版功能

使用 Visual Studio Enterprise 或 Visual Studio Test Professional 时，可以使用 Microsoft 测试管理器的 Visual Studio 实验室管理工具版功能创建和管理实验室环境。

实验室管理工具版会在环境中的每台计算机上自动安装测试代理。  
  
如果你将实验室管理与 System Center Virtual Machine Manager (SCVMM) 结合使用，你还可以在使用实验室环境时获得以下优势：  
  
* **快速重现计算机配置** - 可以存储已配置的虚拟机集合以重新创建典型生产环境 然后你可以在存储的环境的每个新副本上执行每个测试运行。  
  
* **重现 bug 的具体条件** - 当测试运行失败时，可以存储实验室环境的状态副本，然后从生成结构或工作项访问它。  
  
* **同时运行实验室环境的多个副本** - 可以在没有命名冲突的情况下同时运行实验室环境的多个副本。  
  
### <a name="standard-environments-and-scvmm-environments"></a>标准环境和 SCVMM 环境

可以使用 Visual Studio 实验室管理工具版创建两种类型的实验室环境：标准环境和 SCVMM 环境。
但是，每种类型的环境的功能不相同。  
  
> 请注意：实验室管理工具版不支持 SCVMM 2016。 有关 SCVMM 的信息，请参阅 [Virtual Machine Manager](http://go.microsoft.com/fwlink/?LinkId=226332)。 
  
**标准环境：**可混合包含虚拟机和物理计算机。 你还可以向由第三方虚拟化框架托管的标准环境添加虚拟机。 此外，标准环境不需要其他服务器资源，例如 SCVMM 服务器。  
  
**SCVMM 环境：**仅包含由 SCVMM (System Center Virtual Machine Manager) 托管的虚拟机，因此 SCVMM 环境中的虚拟机仅可在 Hyper-V 虚拟化框架上运行。 但是，SCVMM 环境提供标准环境中不提供的以下自动化和管理功能：  
  
- **环境快照：**环境快照包含实验室环境的状态，因此可以快速还原干净的环境或保存已修改的环境状态。 你还可以使用生成-部署-测试工作流自动执行保存和还原环境快照的过程。  
  
- **存储的环境：**可以存储 SCVMM 环境的副本，然后部署该环境的多个副本。  
  
- **网络隔离：**通过网络隔离可以在没有计算机名称冲突的情况下同时运行 SCVMM 环境的多个相同副本。  
  
- **虚拟机模板：**虚拟机模板是删除了其名称和其他标识符的虚拟机。 在 SCVMM 环境中部署 VM 模板时，Microsoft 测试管理器会生成新的标识符。 这使你可以在同一环境或多个环境中部署多个虚拟机的副本，然后同时运行虚拟机。  
  
- **已存储虚拟机：**存储在团队项目库中并包含唯一标识符的虚拟机。  
  
有关这些功能的详细信息，请参阅 [SCVMM 环境的创建和管理指南](https://msdn.microsoft.com/en-gb/library/ee830480.aspx)。  
  
标准环境和 SCVMM 环境支持许多相同功能。 但是，有一些重要的区别需要注意。 下表比较了可用于标准环境和 SCVMM 环境的功能。  
  
|功能|SCVMM 环境|标准环境|  
|----------------|------------------------|---------------------------|  
|**测试**|||  
|运行手动测试|支持|支持|  
|运行代码 UI 和其他自动化测试|支持|支持|  
|使用诊断适配器的文件丰富 bug|支持|支持|  
|**生成部署**|||  
|自动生成-部署-测试工作流|支持|支持|  
|**环境的创建和管理**|||  
|除虚拟机以外，还可使用物理计算机|不支持|支持|  
|使用第三方虚拟机|不支持|支持|  
|在实验室环境中自动将测试代理安装到计算机|支持|支持|  
|使用环境快照保存和部署实验室环境的状态|支持|不支持|  
|从 VM 模板创建实验室环境|支持|不支持|  
|启动/停止/快照环境|支持|不支持|  
|使用环境查看器连接到环境|支持|支持|  
|使用网络隔离同时运行环境的多个副本|支持|不支持|  
  
### <a name="lab-management-concepts"></a>实验室管理概念

以下是一些你在继续之前应该熟悉的其他概念：  
  
|术语|描述|  
|----------|-----------------|  
|实验室中心|可在其中创建和管理实验室环境的 Microsoft 测试管理器区域。|  
|团队项目实验室|已设置的实验室环境的集合，以便你连接到它们并运行其虚拟机。|  
|团队项目库|已存储虚拟机、模板和已存储实验室环境的存档，它已导入团队项目的主机组。 你可以借助 SCVMM 环境使用你的库中的项；但是，你无法将它们直接添加到标准环境。 你无法运行库中的项；但你可以使用它们部署新环境。|  
|已部署环境|已部署到你的团队项目实验室的实验室环境，以便你连接到它并运行它的计算机。|  

#### <a name="related-topics"></a>相关主题

* [规划实验室](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx) 
* [管理实验室](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx) 
* [设置 SCVMM 环境](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx) 
* [将 SCVMM 2008 R2 升级到 SCVMM 2012](upgrade-scvmm-2008-r2-scvmm-2012.md) 
* [管理权限](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx) 
* [更改设置](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx) 
* [疑难解答](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)
  
### <a name="set-up-environments"></a>设置环境

* [生成和发布云环境](use-build-or-rm-instead-of-lab-management.md)
* [标准实验室环境](https://msdn.microsoft.com/en-gb/library/ee390842.aspx)
* [SCVMM（虚拟）环境](https://msdn.microsoft.com/en-gb/library/ee943322.aspx)
* [创建和使用网络独立环境](https://msdn.microsoft.com/en-gb/library/ee518924.aspx)
  
## <a name="see-also"></a>请参阅
  
* [安装和配置测试代理](install-configure-test-agents.md)
* [Visual Studio 实验室管理工具版指南](http://go.microsoft.com/fwlink/?LinkID=230951)  
* [管理用于测试的实验室环境](http://go.microsoft.com/fwlink/?LinkID=252614)  
* [Visual Studio devops + Team Foundation Server 博客](http://go.microsoft.com/fwlink/?LinkID=254496)  

