---
title: "使用 Microsoft.NET Framework 2.0 或 3.0 时仅支持混合的模式调试 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd022d8f0a0e38ffbd7402c69f622df74e24bc30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>仅当使用 Microsoft .NET Framework 2.0 或 3.0 时才支持混合模式调试
低于 2.0 的 Microsoft .NET Framework 版本不支持对 64 位进程进行混合模式调试。 这意味着，当您进行调试时，无法从托管代码单步执行到本机代码，也无法从本机代码单步执行到托管代码。  
  
 若要解决此问题，您可以：  
  
-   更新项目以使用 Microsoft .NET Framework 2.0 或 3.0。  
  
-   在单独的调试会话中调试托管代码和本机代码。  
  
-   作为 32 位进程调试混合代码，如下面的过程所述。  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>将操作系统更改为 32 位（Visual Basic 或 C#）  
  
1.  在**解决方案资源管理器**，右键单击你的项目，然后单击**属性**的快捷菜单中。  
  
2.  在属性页中，单击**编译**或**调试**选项卡。  
  
3.  单击**平台**，然后选择**x86**从平台列表。  
  
     默认情况下，Visual Basic 和 C# 编译器生成要在任何 CPU 上运行的代码。 在 64 位计算机上，这些二进制代码作为 64 位进程运行。 若要在 32 位进程中运行，必须选择**Win32**，而不**AnyCPU**。  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>将操作系统更改为 32 位 (C/C++)  
  
1.  在**解决方案资源管理器**，右键单击你的项目，然后单击**属性**的快捷菜单中。  
  
     在属性页中，单击**平台**，然后选择**Win32**从平台列表。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请参阅[设置 SQL 调试](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)。  
  
## <a name="see-also"></a>另请参阅  
 [调试 64 位应用程序](../debugger/debug-64-bit-applications.md)