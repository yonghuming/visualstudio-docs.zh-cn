---
title: "SDI 服务器应用程序 |Microsoft 文档"
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 089eeada5f3d9d392aff7768ed3f5b813ef8f772
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sdi-server-applications"></a>SDI 服务器应用程序
如果你正在调试的 SDI 服务器应用程序，你必须指定`/Embedding`或`/Automation`中**命令行自变量**中的属性*项目*属性页对话框中，C/c + +，C# 中，或Visual Basic 项目。  
  
 使用这些命令行自变量，调试器可以像从容器中启动服务器应用程序一样启动它。 从程序管理器或文件管理器启动容器将导致容器使用在调试器中启动的服务器实例。  
  
## <a name="finding-the-command-line-arguments-property"></a>查找“命令行自变量”属性  
 访问*项目*属性页对话框中，右键单击解决方案资源管理器中的项目，然后从快捷菜单选择属性。 若要找到“命令行自变量”属性，请展开“配置属性”类别并单击“调试”页。  
  
## <a name="see-also"></a>另请参阅  
 [调试 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [如何：调试 COM 服务器](../debugger/how-to-debug-com-servers.md)