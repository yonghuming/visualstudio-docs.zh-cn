---
title: "无可用的源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02c91f5e5a55e82633d89aa7209321126271e8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="no-source-available"></a>无可用的源
你的项目不包含你尝试查看代码的源代码。 原因通常双击中没有源代码的模块**调用堆栈窗口**或**线程窗口**。 可以继续调试，但不能使用源窗口设置断点并在此位置执行其他操作。 如果你需要设置断点，使用**反汇编窗口**相反。  
  
 在解决方案属性页中，可以更改调试器查找源文件的目录，并通知调试器忽略选定的源文件。 请参阅[调试源通用的属性，解决方案属性页对话框中](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。  
  
 **浏览并找到源代码**  
 单击此链接以打开对话框，可从中浏览并找到源代码。  
  
 **显示反汇编**  
 将启动**反汇编窗口**。  
  
 **始终显示缺少的源文件的反汇编**  
 选择此选项以显示**反汇编窗口**自动没有源可用时。 此设置还可以更改在**选项**对话框中，**调试**类别，**常规**页上，通过选中或清除**显示反汇编如果源不可用**。  
  
## <a name="see-also"></a>另请参阅  
 [调试源通用的属性，解决方案属性页对话框中](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll（SOS 调试扩展）](/dotnet/framework/tools/sos-dll-sos-debugging-extension)