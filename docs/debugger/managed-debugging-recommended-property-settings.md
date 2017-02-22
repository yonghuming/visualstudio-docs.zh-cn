---
title: "托管调试：推荐的属性设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试 [Visual Studio], 托管"
  - "调试托管代码, 推荐的属性设置"
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 托管调试：推荐的属性设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

某些属性应该在所有托管调试方案中采用相同的设置。  
  
 以下各表显示了建议的属性设置。  
  
 未在此处列出的属性可能在不同的托管项目类型之间会有所不同。  例如，**“启动操作”**在 Windows 窗体项目中和在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 项目中会采用不同的设置。  
  
### “生成”\(C\#\) 或“编译”\(Visual Basic\) 选项卡上的配置属性  
  
|**属性名**|**设置**|  
|-------------|------------|  
|**定义 DEBUG 常数**|C\# 和 F\#：将复选框设置为已选中。  这使您的应用程序能够使用 Debug 类。|  
|**定义 TRACE 常数**|C\# 和 F\#：将复选框设置为已选中。  这使您的应用程序能够使用 Trace 类。|  
|**优化代码**|C\#、F\# 和 Visual Basic：设置为 false。  优化代码更难调试，因为生成的指令与源代码并不直接对应。  如果发现程序具有只出现在优化代码中的 bug，则可以打开此设置，但应记住**“反汇编”**窗口中显示的代码是从与代码编辑器中的内容可能不匹配的优化源生成的。  若要调试优化代码，必须关闭“仅我的代码”。（请参阅[限制单步执行“仅我的代码”](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)）。<br /><br /> 有关详细信息，请参阅 [C\# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md) 或 [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)。|  
|**输出路径**|设置为 bin\\Debug\\。|  
|**高级编译选项**|仅 Visual Basic。  单击**“高级”**设置下表中介绍的高级属性。|  
  
### “高级编译器设置”对话框  
  
|**属性名**|**设置**|  
|-------------|------------|  
|**启用优化**|可基于上表中的**“优化代码”**选项中指定的原因将其设置为 false。|  
|**生成调试信息**|选择此复选框可在编译时设置 \/DEBUG 标志，该标志能够生成可用于调试的信息。|  
|**定义 DEBUG 常数**|选择此复选框可定义 `DEBUG` 常数，该常数使应用程序可以使用 <xref:System.Diagnostics.Debug> 类。|  
|**定义 TRACE 常数**|选择此复选框可定义 `TRACE` 常数，该常数使应用程序可以使用 <xref:System.Diagnostics.Trace> 类。|  
  
## 请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md)   
 [C\#、F\# 和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)