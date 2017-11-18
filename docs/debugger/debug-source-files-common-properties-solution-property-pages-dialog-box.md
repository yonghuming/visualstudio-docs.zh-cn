---
title: "调试源通用的属性，解决方案属性页对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96ca9ef63a3823b942a6d7a160c31473f5db8962
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>“解决方案属性页”对话框 ->“通用属性”->“调试源文件”
该属性页指定调试解决方案时调试器查找源文件的位置。  
  
 访问**调试源文件**属性页中，右键单击你的解决方案中**解决方案资源管理器**和选择**属性**从快捷菜单。 展开**通用属性**文件夹，然后单击**调试源文件**页。  
  
 **包含源代码的目录**  
 包含在调试解决方案时调试器搜索源文件的目录的列表。 还可搜索指定目录的子目录。  
  
 **不查找这些源文件**  
 输入不希望调试器读取的任何文件的名称。 如果调试器在以上指定的某个目录中找到这些文件之一，它将忽略该文件。 如果**查找源**时进行调试，而您单击对话框中出现**取消**，要搜索的文件获取添加到此列表中，以使调试器不再继续搜索该文件。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)