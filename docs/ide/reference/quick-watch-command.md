---
title: "“快速监视”命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: b9b6af3a8db0aef28a7704f8e266e1610b436ba6
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="quick-watch-command"></a>“快速监视”命令
在[快速监视](../../debugger/watch-and-quickwatch-windows.md)窗口的“表达式”字段中显示选定或指定的文本。 可使用此对话框计算调试器所识别的变量或表达式的当前值或计算寄存器的内容。 此外，可更改任何非常量变量的值或任何寄存器的内容。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>参数  
 `text`  
 可选。 要添加到“快速监视”对话框的文本。  
  
## <a name="remarks"></a>备注  
 如果忽略了 `text`，则光标处当前选中的文本或字词将添加到“监视”窗口。  
  
## <a name="example"></a>示例  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中使用“监视”窗口和“快速监视”窗口对变量设置监视](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)
