---
title: "上下文参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 642b0cecd700d66db30385f149a30cd09113fc7d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="context-parameters"></a>上下文参数
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)，你可以添加到向导**新项目**，**添加新项**，或**添加子项目**对话框。 添加的向导位于**文件**菜单或通过右键单击中的项目**解决方案资源管理器**。 IDE 将上下文参数传递给该向导的实现。 当 IDE 调用向导时，上下文参数定义项目的状态。  
  
 在 IDE 启动向导，通过设置<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>对 IDE 的调用中的标志<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>项目的方法。 设置时，项目必须导致`IVsExtensibility::RunWizardFile`要通过使用已注册的向导名称或 GUID 和其他 IDE 传递给它的上下文参数执行方法。  
  
## <a name="context-parameters-for-new-project"></a>新项目的上下文参数  
  
|参数|描述|  
|---------------|-----------------|  
|`WizardType`|已注册的向导类型 (<xref:EnvDTE.Constants.vsWizardNewProject>) 或指示向导的类型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]实现，该向导的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|一个字符串，它唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目名称。|  
|`LocalDirectory`|使用项目文件的本地位置。|  
|`InstallationDirectory`|目录路径[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安装。|  
|`FExclusive`|布尔型标志，指示项目应关闭打开的解决方案。|  
|`SolutionName`|而无需的目录部分或扩展名为.sln 的解决方案文件的名称。 .Suo 文件名称也由使用`SolutionName`。 当此参数不为空字符串时，该向导使用<xref:EnvDTE._Solution.Create%2A>之前添加与项目<xref:EnvDTE._Solution.AddFromTemplate%2A>。 如果此名称为空字符串，使用<xref:EnvDTE._Solution.AddFromTemplate%2A>而不调用<xref:EnvDTE._Solution.Create%2A>。|  
|`Silent`|布尔值，该值指示是否应以无提示方式运行向导就像**完成**已单击 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>用于的上下文参数添加新项  
  
|参数|描述|  
|---------------|-----------------|  
|`WizardType`|已注册的向导类型 (<xref:EnvDTE.Constants.vsWizardAddItem>) 或指示向导的类型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]实现，该向导的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|一个字符串，它唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目名称。|  
|`ProjectItems`|包含工作项目文件的本地位置。|  
|`ItemName`|要添加的项的名称。 此名称是默认文件名称或从类型的用户的文件名称**添加项**对话框。 该名称基于.vsdir 文件中设置的标志。 名称可以是 null 值。|  
|`InstallationDirectory`|目录路径[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安装。|  
|`Silent`|布尔值，该值指示是否应以无提示方式运行向导就像**完成**已单击 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>添加子项目的上下文参数  
  
|参数|描述|  
|---------------|-----------------|  
|`WizardType`|已注册的向导类型 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) 或指示向导的类型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]实现，该向导的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|一个字符串，它唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目名称。|  
|`ProjectItems`|指向`ProjectItems`向导进行操作的集合。 此指针传递到基于项目层次结构选择该向导。 用户通常会选择在其中放入该项目的文件夹，然后调用项目的**添加项**对话框。|  
|`LocalDirectory`|使用项目文件的本地位置。|  
|`ItemName`|要添加的项的名称。 此名称是默认文件名称或从类型的用户的文件名称**添加项**对话框。 该名称基于.vsdir 文件中设置的标志。 名称可以是 null 值。|  
|`InstallationDirectory`|目录路径[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安装。|  
|`Silent`|布尔值，该值指示是否应以无提示方式运行向导就像**完成**已单击 (`TRUE`)。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [自定义参数](../../extensibility/internals/custom-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [向导 (。Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [用于启动向导的上下文参数](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)