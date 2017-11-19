---
title: "托管调试： 推荐的属性设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f763decca7a80a7a7fc5bb86f94a76cd3eb2679c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managed-debugging-recommended-property-settings"></a>托管调试：推荐的属性设置
某些属性应该在所有托管调试方案中采用相同的设置。  
  
 以下各表显示了建议的属性设置。  
  
 未在此处列出的属性可能在不同的托管项目类型之间会有所不同。 例如，**启动操作**将比在 Windows 窗体项目中以不同方式设置[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]项目。  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>“生成”(C#) 或“编译”(Visual Basic) 选项卡上的配置属性  
  
|**属性名称**|**设置**|  
|-----------------------|-----------------|  
|“定义 DEBUG 常量”|C# 和 F#：将复选框设置为已选中。 这使您的应用程序能够使用 Debug 类。|  
|“定义 TRACE 常量”|C# 和 F#：将复选框设置为已选中。 这使您的应用程序能够使用 Trace 类。|  
|**优化代码**|C#、F# 和 Visual Basic：设置为 false。 优化代码更难调试，因为生成的指令与源代码并不直接对应。 如果发现程序具有只在优化代码中出现的 bug，则可以打开此设置，但应记住中显示的代码**反汇编**窗口从可能与在代码中看到的内容不匹配的优化源生成编辑器。 若要调试优化代码，必须关闭“仅我的代码”。 (请参阅[限制单步执行仅我的代码](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code))。<br /><br /> 有关详细信息，请参阅[C# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)或[Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)。|  
|“输出路径”|设置为 bin\Debug\\。|  
|**高级的编译选项**|仅 Visual Basic。 单击**高级**设置下表中所述的高级的属性。|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>“高级编译器设置”对话框  
  
|**属性名称**|**设置**|  
|-----------------------|-----------------|  
|**启用优化**|中指定的原因，设置为 false**优化代码**前面的表中的选项。|  
|**生成调试信息**|选择此复选框可在编译时设置 /DEBUG 标志，该标志能够生成可用于调试的信息。|  
|“定义 DEBUG 常量”|选择此复选框可定义 `DEBUG` 常数，该常数使应用程序可以使用 <xref:System.Diagnostics.Debug> 类。|  
|“定义 TRACE 常量”|选择此复选框可定义 `TRACE` 常数，该常数使应用程序可以使用 <xref:System.Diagnostics.Trace> 类。|  
  
## <a name="see-also"></a>另请参阅  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)（C#、F# 和 Visual Basic 项目类型）