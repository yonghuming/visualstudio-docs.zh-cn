---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
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
ms.openlocfilehash: 826740ff2c56f50426d51e91fe9ccf8cdcb99081
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
移除与指定外接程序关联的命令和命令用户界面。  
  
## <a name="syntax"></a>语法  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>参数  
 `AddIn`  
 可选。 外接程序的命令名称。  
  
## <a name="remarks"></a>备注  
 默认情况下，外接程序的命令名称等于 *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>*，并在 Connect.cs 中显示为 `Exec` 方法的 `commandName` 参数。 还可以通过开始在 Visual Studio 的“命令”窗口中键入外接程序的名称并使用 Intellisense 填充其余部分来验证命令名称。  
  
## <a name="example"></a>示例  
 以下示例启动 Visual Studio 并阻止 `MyAddin` 外接程序在启动时运行。  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>另请参阅  
 [个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)