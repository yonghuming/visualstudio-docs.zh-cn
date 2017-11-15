---
title: "使用 Build Management 或 Release Management 进行自动测试 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 8d843800666ae53a686a18fcab28d02eb4c16743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>使用 Build Management 或 Release Management（而不是实验室管理工具版）进行自动测试

如果使用 Microsoft 测试管理器 (MTM) 和实验室管理工具版进行自动测试或生成-部署-测试自动化，请参阅本主题，本主题介绍了如何使用 Team Foundation Server (TFS) 和 Visual Studio Team Services 中的[生成和发布](https://www.visualstudio.com/team-services/continuous-integration/)功能实现相同的目的：

* [生成-部署-测试自动化](#bdtautomation)

* [SCVMM 环境的自助式管理](#managescvmm)

Build Management 和 Release Management 不支持自助式创建网络隔离的 SCVMM 环境，并且以后也不计划提供此支持。 但是，有一些[建议的替代方法](#isolatedenvir)。

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>生成-部署-测试自动化

MTM 和实验室管理工具版依赖 XAML 生成定义来自动生成、部署和测试应用程序。
XAML 生成依赖于在 MTM 中创建的各种构造（例如实验室环境、测试套件和测试设置）和各种基础结构组件（例如生成控制器、生成代理、测试控制器和测试代理）来实现此目标。 可使用 TFS 和 Team Services 中的 Build Management 或 Release Management 以更少的步骤来实现相同的目的。

| 步骤 | 使用 XAML 生成 | 使用 Build Management 或 Release Management |
|-------|----------------------|-----------------|
| 确定部署生成和运行测试的计算机。 | 使用这些计算机在 MTM 中创建标准实验室环境。 | 无 |
| 确定要运行的测试。 | 在 MTM 中创建测试套件、创建测试用例并将自动化与每个测试用例关联。 在 MTM 中创建测试设置，标识计算机在运行测试的实验室环境中的角色。 | 如果打算通过测试计划管理测试，则以相同的方式在 MTM 中创建自动测试套件。 如果想从生成产生的测试二进制文件直接运行测试，则可以跳过此步骤。 两种情况下都无需创建测试设置。 |
| 自动部署和测试。 | 使用 LabDefaultTemplate.*.xaml 创建 XAML 生成定义。 在生成定义中指定生成、测试套件和实验室环境。 | 使用单一环境创建[生成定义或发布定义](https://www.visualstudio.com/team-services/continuous-integration/)。 使用命令行任务从 XAML 生成定义运行相同的部署脚本，并使用“测试代理部署”和“运行功能测试”任务运行自动测试。 将一系列计算机及其凭据指定为这些任务的输入。 |

在此方案中使用 Build Management 或 Release Management 的优势包括：

* 不需要生成控制器或测试控制器。
* 生成或发布过程中会通过任务安装测试代理。
* 可以轻松地自定义部署步骤。 不再受到使用单一脚本的限制。 还可利用产品和 Visual Studio Marketplace 中提供的许多任务。
* 无需维护测试套件。 可从二进制文件直接运行测试。
* 每个生成或发布中运行的测试会提供更丰富的内联报告体验。
* 可以跟踪每个环境上当前部署和测试的资产类型（发布、生成、工作项、提交）。
* 可自定义和扩展自动化，并轻松部署到多个测试环境，甚至生产环境。
* 可计划在签入或提交时，或在每天的特定时间执行自动化操作。

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 环境的自助式管理

[Microsoft 测试管理器的实验室中心](https://msdn.microsoft.com/library/dd997438.aspx)可以管理环境模板库，并使用 [SCVMM 服务器](https://technet.microsoft.com/system-center-docs/vmm/vmm)根据需要配置环境。

实验室中心的自助式预配功能有两个不同的目标：

* 通过更简单的方法来管理基础结构。 举例来说，基础结构管理包括管理 VM 模板和环境模板，以及自动创建专用网络，以将克隆环境相互隔离。

* 让团队能够通过更简单的方法在其测试和部署活动中使用虚拟机。 举例来说，简单的使用方式包括使实验室环境可通过同一团队项目安全模型进行访问，在测试方案中以集成方式使用这些虚拟机。

但是，虽然随着时代发展现已具有更丰富的公有和私有云管理系统，例如 [Microsoft Azure](https://azure.microsoft.com/) 和 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)，但 TFS 2017 和更高版本中的基础结构管理功能仍然没有变化。 相反，关注的问题仍然是如何方便地使用此类云基础结构管理的资源。

下表总结了用于在实验室中心执行的典型活动，以及如何通过 SCVMM 或 Azure（适用于基础结构管理活动）或通过 TFS 和 Team Services（适用于测试或部署活动）完成这些活动：

| 步骤 | 使用实验室中心 | 使用 Build Management 或 Release Management |
|-------|----------------------|-----------------|
| 管理环境模板库。 | 创建实验室环境。 在虚拟机上安装必要的软件。 进行系统准备，并将环境存储为库中的模板。 | 使用 SCVMM 管理控制台直接创建和管理虚拟机模板或服务模板。 使用 Azure 时，从 [Azure Marketplace](https://azure.microsoft.com/marketplace/) 或 [Azure 快速入门模板](https://azure.microsoft.com/documentation/templates/)中选择一个预定义的 [Azure 资源管理器模板](https://azure.microsoft.com/documentation/templates/)。 |
| 创建实验室环境。 | 在库中选择一个环境模板并部署该模板。 提供自定义虚拟机配置所需的参数。 | 使用 SCVMM 管理控制台根据模板直接创建虚拟机或服务实例。 使用 Azure 门户直接创建资源。 或使用环境创建发布定义。 使用 Azure 任务或 [SCVMM 集成扩展](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)中的任务创建新虚拟机。 创建此定义的新发布相当于在实验室中心中创建新环境。 |
| 连接到计算机。 | 在“环境查看器”中打开实验室环境。 | 使用 SCVMM 管理控制台直接连接到虚拟机。 或者使用虚拟机的 IP 地址或 DNS 名称打开远程桌面会话。 |
| 执行环境的检查点，或将环境还原到干净的检查点。 | 在“环境查看器”中打开实验室环境。 选择执行检查点或还原到之前的检查点的选项。 | 使用 SCVMM 管理控制台直接对虚拟机执行这些操作。 或者若要在更大的自动化过程中执行这些步骤，则在发布定义的环境中包括 [SCVMM 集成扩展](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)中的检查点任务。 |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>自助式创建网络隔离环境

网络隔离实验室环境是一系列 SCVMM 虚拟机，这些虚拟机可以在不引起网络冲突的情况下进行安全克隆。 根据使用一组网络接口卡在专用网络中配置虚拟机和使用另一组网络接口卡在公用网络中配置虚拟机的一系列说明，在 MTM 中完成此操作。

随着时代发展现已具有更丰富的公有和私有云管理系统，例如 [Microsoft Azure](https://azure.microsoft.com/) 和 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)，因此可以直接更多地依赖云管理工具实现类似功能。 Build Management 和 Release Management 中没有实现此目标的等效方法。

如果需要网络隔离，建议考虑以下替代方法：

* 网络隔离有一个动机就是简化多个克隆的配置。 每个克隆都是原始对象的精确副本，因此计算机名称和配置设置保留原样，这样便可轻松设置新环境。 但是，这种优势在生命周期（例如在生产中）后期会导致出现问题，因为最终部署应用程序的方式不同。 可改为考虑按设置生产的相同方式设置新环境，并避免使用网络隔离。

* 使用 [Microsoft Azure](https://azure.microsoft.com/) 等公有云基础结构满足测试需求。 轻松使用 [Azure Marketplace](https://azure.microsoft.com/marketplace/) 或 [Azure 快速入门模板](https://azure.microsoft.com/documentation/templates/)提供的 [Azure 资格管理器模板](https://azure.microsoft.com/documentation/templates/)，只需通过代理或“跳转盒”即可设置通过私有网络连接，并向公用网络公开的一系列虚拟机。
