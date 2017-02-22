---
title: "SDI 服务器应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SDI 服务器应用程序"
  - "SDI 服务器应用程序, 调试"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDI 服务器应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果正在调试 SDI 服务器应用程序，对于 C\/C\+\+、C\# 或 Visual Basic 项目，必须在“*Project* 属性页”对话框中的**“命令行参数”**属性中指定 `/Embedding` 或 `/Automation`。  
  
 使用这些命令行参数，调试器可以像从容器中启动服务器应用程序一样启动它。  从程序管理器或文件管理器启动容器将导致容器使用在调试器中启动的服务器实例。  
  
## 查找“命令行参数”属性  
 若要访问“*Project* 属性页”对话框，请在“解决方案资源管理器”中右键单击您的项目，然后从快捷菜单中选择“属性”。  若要找到“命令行参数”属性，请展开“配置属性”类别并单击“调试”页。  
  
## 请参阅  
 [调试 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [如何：调试 COM 服务器](../Topic/How%20to:%20Debug%20COM%20Servers.md)