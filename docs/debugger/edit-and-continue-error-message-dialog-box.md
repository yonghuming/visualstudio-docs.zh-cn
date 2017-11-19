---
title: "编辑并继续错误消息对话框 |Microsoft 文档"
ms.custom: 
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21d72c5bb4bacaed0324d688d96c663e3153b6a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="edit-and-continue-error-message-dialog-box"></a>“编辑并继续”错误消息对话框
当在支持编辑并继续的语言中进行调试时，会出现此对话框但**编辑并继续**不可用于所做的代码更改的类型。 此框中的错误消息提供了更加详细的说明。 此对话框出现的可能原因包括：  

-   尝试编辑 SQL Server 代码。

-   尝试编辑优化的代码。 （你可能需要从发布版本切换到调试版本。）

-   你尝试运行时编辑代码 (而不是在暂停时在调试器中)。 请尝试[设置断点](../debugger/using-breakpoints.md)和编辑代码在暂停时。

-   尝试在启用非托管调试时编辑托管代码。 编辑并继续不适用于[混合模式调试](../debugger/how-to-debug-in-mixed-mode.md)。

-   你所做更改的代码中您的编程语言不支持编辑并继续。 有关详细信息，请参阅主题中的不受支持的代码更改[C#](../debugger/supported-code-changes-csharp.md)， [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)，和[c + +](../debugger/supported-code-changes-cpp.md)。
  
-   尝试编辑而不是从启动附加到的程序中的代码**调试**菜单。  
  
-   尝试在调试 Dr. Watson 转储期间编辑Watson 转储。  
  
-   尝试编辑在发生未经处理的异常的代码和选项"**展开调用堆栈上未经处理的异常**"未选中。  
  
-   尝试在调试嵌入的运行时应用程序时编辑代码。
  
-   尝试编辑托管的代码使用 4.5.1 之前, 的.NET Framework 版本，且目标为 64 位应用程序。 如果希望使用“编辑并继续”，必须将目标平台设置为 x86 (*projectname* **属性**，**编译**选项卡上，**高级编译器**设置。)。  
  
-   尝试编辑在调试过程中修改过并已重新加载的程序集中的代码。  
  
-   尝试编辑尚未加载的程序集中的代码。  
  
-   开始调试旧版本的应用程序（由于新版本具有生成错误）。
  
## <a name="uielement-list"></a>UIElement 列表  
 **还行**  
 退出对话框并取消之前的编辑尝试。  
  
## <a name="see-also"></a>另请参阅  
 [C + + 编辑并继续博客文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [受支持的代码更改 (C++)](../debugger/supported-code-changes-cpp.md)