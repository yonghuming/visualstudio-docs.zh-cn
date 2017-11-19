---
title: "用于管理部署项目配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87098c362e5b37690e2ab3116ffca431d58f129d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-managing-deployment"></a>用于管理部署的项目配置
部署是以物理方式将从生成过程的输出项移动到预期位置用于调试和安装的行为。 例如，Web 应用程序可能会在本地计算机上生成并将其放在服务器上。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支持项目的两种方法可以参与部署：  
  
-   作为部署过程的主题。  
  
-   作为部署过程中的管理器。  
  
 可以部署解决方案之前，您必须首先添加一个部署项目来配置部署选项。 如果不存在部署项目，你系统会要求你想要创建一个，当你选择**部署解决方案**从**生成**菜单或右键单击该解决方案。 单击**是**打开**添加新项目** 癸杠**远程部署向导**中选择项目。  
  
 远程部署向导会询问您的应用 （Windows 或 Web） 的类型、 要包含的项目输出组、 你想要包括，任何其他文件和你想要部署到远程计算机。 该向导的最后一页显示所选选项的摘要。  
  
 主题的部署过程的项目会生成输出项必须转移到备用的环境。 这些输出用作参数说明项<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>接口，其主要用途如果以允许组输出到的项目。 有关详细信息的实现与相关`IVsProjectCfg2`，请参阅[输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)。  
  
 部署项目、 管理部署过程，启用部署命令，并选择此命令时做出响应。 部署项目实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>接口以执行部署，并对进行调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>接口报表部署状态事件。  
  
 配置可以指定对其生成或部署操作影响的依赖关系。 生成或部署依赖关系是，必须生成或部署之前或之后的配置自己生成或部署的项目。 描述生成项目之间的依赖项都<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>接口，并在部署依赖关系<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>接口。 有关详细信息，请参阅[构建的项目配置](../../extensibility/internals/project-configuration-for-building.md)。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [用于输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)