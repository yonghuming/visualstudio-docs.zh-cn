---
title: "通过使用修改独立的 Shell。Pkgundef 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>通过使用修改独立的 Shell。Pkgundef 文件
您可以修改.pkgundef 文件以排除指定的注册表条目从独立的 shell 应用程序。 通常情况下，第一次在计算机上，启动的应用程序的 Visual Studio shell 将复制现有的 Visual Studio 注册表条目到应用程序的根注册表项。 这包括对 VSPackages 迁移当前安装的任何引用。  
  
 若要从独立的 shell 应用程序中排除特定的注册表项，将添加到包键，再按该条目的应用程序.pkgundef 文件。 项和条目表示一样.pkgdef 文件;也就是说，作为 [$RootKey$] 或 [$RootKey$\\*子项*] 和"*条目*"=*值*，其中*子项*是要影响的子项*条目*是要删除的项和*值*是`""`或`dword:00000000`。  
  
 若要从注册表项中排除多个项，只是列出密钥一次后, 跟每个条目以排除的行。  
  
 若要从独立的 shell 应用程序排除整个注册表项，向应用程序.pkgundef 文件中添加项，但未指定该注册表项任何注册表项。  
  
 可以将注释添加到.pkgundef 文件。 单行注释必须具有两个斜杠作为前两个字符。  
  
 例如，若要删除**连接到数据库**和**连接到服务于 r**命令的**工具**菜单上，可以取消注释行︰  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 并添加行︰  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 向应用程序的.pkgundef 文件。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 功能的包 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自定义独立的 Shell](../extensibility/customizing-the-isolated-shell.md)
