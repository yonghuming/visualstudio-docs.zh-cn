---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "通过使用修改独立的 Shell。Pkgundef 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4c0f46924c2c828158960a924faa031be0fd14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>通过使用修改独立的 Shell。Pkgundef 文件
你可以修改.pkgundef 文件以排除指定的注册表条目从独立的 shell 应用程序。 通常情况下，首次应用程序启动的计算机，Visual Studio shell 将复制现有的 Visual Studio 注册表条目到应用程序的根注册表项。 这包括对当前安装的 Vspackage 的任何引用。  
  
 若要从独立的 shell 应用程序中排除特定的注册表项，将添加到应用程序.pkgundef 文件包密钥后跟该条目。 项和条目表示一样.pkgdef 文件;也就是说，作为 [$RootKey$] 或 [$RootKey$\\*子项*] 和"*条目*"=*值*，其中*子项*是要影响的子项*条目*是要删除的项和*值*是`""`或`dword:00000000`。  
  
 若要从注册表项中排除多个条目，只列出密钥一次，跟要排除的每个条目的行。  
  
 若要从独立的 shell 应用程序中排除整个注册表项，将密钥添加到应用程序.pkgundef 文件，但未指定该注册表项的任何注册表项。  
  
 你可以将注释添加到.pkgundef 文件中。 单行注释必须具有两个斜杠作为前两个字符。  
  
 例如，若要删除**连接到数据库**和**连接到提供 r**上的命令**工具**菜单上，你可以取消注释行：  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 并添加行：  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 到应用程序的.pkgundef 文件。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 功能的包 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自定义独立 Shell](../extensibility/customizing-the-isolated-shell.md)