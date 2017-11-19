---
title: "自定义参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f04251ea8141d07a52499beae46b2881814eec9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-parameters"></a>自定义参数
启动向导后，自定义参数控制的操作的向导。 相关的.vsz 文件提供了通过集成的开发环境 (IDE) 打包和启动向导时作为数组的字符串传递到向导的用户定义参数的数组。 然后，该向导分析字符串的数组，并使用的信息来控制的实际操作的向导。 这种方式，具体取决于.vsz 文件的内容的功能可以自定义向导。  
  
 启动向导时，上下文参数，另一方面，定义项目的状态。 有关详细信息，请参阅[上下文参数](../../extensibility/internals/context-parameters.md)。  
  
 下面是一个具有自定义参数的.vsz 文件示例：  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 文件作者添加参数的值。 当用户选择**新项目**或**添加新项**文件菜单上或通过右键单击中的项目**解决方案资源管理器**，IDE 收集以下这些值转换为数组字符串。 IDE 然后调用项目的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>方法替换<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>标志集和项目调用<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>负责运行向导并将结果返回的方法。  
  
 向导负责分析字符串的数组，并相应地对字符串起作用。 在这种方式，通过实现自定义参数可以创建执行各种功能的一个向导。 换而言之，一个向导无法具有三个不同.vsz 文件。 每个文件将传递不同的自定义的参数来控制在各种情况下向导行为集。  
  
 有关详细信息，请参阅[向导 (。Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)