---
title: "如何： 启用和禁用编辑并继续 （C#、 VB、 c + +） |Microsoft 文档"
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
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724851fcd78050d3502cdec4369c7c6a79c9419f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>如何： 启用和禁用编辑并继续 （C#、 VB、 c + +）
你可以禁用或启用在编辑并继续**选项**在设计时的对话框。 无法在调试过程中更改此设置。  
  
“编辑并继续”仅在调试版本中起作用。 对于本机 C++，“编辑并继续”需要使用 /INCREMENTAL 选项。 有关 c + + 中的功能要求的详细信息，请参阅此[博客文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)和[编辑并继续 （Visual c + +）](../debugger/edit-and-continue-visual-cpp.md)。
  
#### <a name="to-enabledisable-edit-and-continue"></a>启用/禁用“编辑并继续”  
  
1.  如果要在调试会话中，停止调试 (**Shift + F5**)。

2.  打开调试选项页 (**工具 > 选项 > 调试**)。
  
3.  选择**常规**，向下滚动到**编辑并继续**类别 （右窗格）。  
  
4.  若要启用，请选择**启用编辑并继续**复选框。 若要禁用它，请清除该复选框。  
  
    > [!NOTE]
    >  如果启用了 IntelliTrace 并且收集 IntelliTrace 事件和调用信息，则会禁用“编辑并继续”。 有关详细信息，请参阅[IntelliTrace](../debugger/intellitrace.md)。

5. （C + +）若要启用，请选择**启用本机编辑并继续**。 若要禁用它，请清除该复选框。

6. （C + +）设置对于本机代码的其他选项。

    - **将更改应用上继续 （仅限本机）**  
        在从中断状态继续该过程时，Visual Studio 会自动编译并应用你所做的任何未完成的代码更改。 如果未选择，你可以选择使用调试菜单下的"应用代码更改"项来应用更改。  
  
    - **就陈旧的代码 （仅限本机），则发出警告**  
        收到关于陈旧代码的警告。 
  
7.  单击“确定”。    
  
## <a name="see-also"></a>另请参阅  
 [编辑并继续](../debugger/edit-and-continue.md)