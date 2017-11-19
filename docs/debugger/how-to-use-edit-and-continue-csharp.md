---
title: "如何： 使用编辑并继续 (C#) |Microsoft 文档"
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
helpviewer_keywords: Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec66bd21eb119c348391f191f23570e66119122f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用“编辑并继续”(C#)
使用 C# 的“编辑并继续”，可以一边进行调试一边在中断模式下更改代码。 不必停止并重新启动调试会话即可应用更改。  
  
 编辑并继续自动调用时在中断模式下，进行更改，然后选择调试器执行命令，如**继续**，**步骤**，或**设置下一语句**，或评估调试器窗口中的函数。  
  
> [!NOTE]
>  调试优化代码、 混合的本机/托管代码或 SQL Server 公共语言运行时 (CLR) 集成代码时不支持编辑并继续。 其他不支持的方案的信息，请参阅[支持的代码更改 （C# 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。 如果你尝试在这些情况下，不支持一个对话框，其中说明编辑并继续调试器显示之一应用代码更改。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>若要调用编辑并继续自动  
  
1.  在中断模式下，对你的源代码中进行更改。  
  
2.  从**调试**菜单上，单击**继续**，**步骤**，或**设置下一语句**或评估调试器窗口中的函数。  
  
     编译新代码，并继续新的代码进行调试。 编辑并继续不支持某些更改。 有关详细信息，请参阅[支持的代码更改 （C# 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。  
  
### <a name="to-enabledisable-edit-and-continue"></a>启用/禁用“编辑并继续”  
  
1.  在 **“工具”** 菜单上，单击 **“选项”**。  
  
2.  在**选项**对话框框中，展开**调试**节点，然后选择**编辑并继续**。  
  
3.  在**选项**对话框**编辑并继续**页上，选中或清除**启用编辑并继续**复选框。  
  
     当你重新启动调试会话时，该设置将生效。  
  
## <a name="see-also"></a>另请参阅  
 [编辑并继续 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [受支持的代码更改 （C# 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)   