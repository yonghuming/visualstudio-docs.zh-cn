---
title: "自定义参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "向导中，自定义参数"
  - "自定义参数"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 自定义参数
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

，请在向导启动后，自定义参数控件向导的操作。  相关 .vsz 文件提供集成开发环境 \(ide\) 打包并传递给向导 \(IDE\)为字符串数组的用户定义的参数，用于在向导启动时。  向导将分析字符串数组并使用该信息控件向导的实际操作。  这样，向导可以根据 .vsz 文件的内容自定义功能。  
  
 ，用于在向导启动时，上下文参数，另一方面，定义项的状态。  有关更多信息，请参见 [上下文参数](../../extensibility/internals/context-parameters.md)。  
  
 以下具有自定义参数 .vsz 文件的示例:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .vsz 文件的作者添加参数的值。  当用户选择 **新项目** 或 **添加新项目** 在 " 文件 " 菜单或通过右击一个项目。 **解决方案资源管理器**， IDE 收集这些值设置为字符串数组。  IDE 然后调用与设置为的 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 标志的项目的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 方案，并且，如果该项对运行向导并返回结果负责的 <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> 方法。  
  
 向导负责正确分析字符串数组和操作字符串。  这样，通过实现自定义参数可以创建执行各种功能的向导。  换言之，一个向导可能有三种 .vsz 文件。  每个文件传递不同设置自定义参数控件向导的行为在各种情况。  
  
 有关更多信息，请参见 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)