---
title: "ShowWebBrowser 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser 命令"
  - "View.ShowWebBrowser 命令"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ShowWebBrowser 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在集成开发环境 \(IDE\) 内或 IDE 外显示在 Web 浏览器窗口中指定的 URL。  
  
## 语法  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## 参数  
 `URL`  
 必选。  网站的 URL（统一资源定位器）。  
  
## 开关  
 \/new  
 可选。  指定在 Web 浏览器的新实例中显示页。  
  
 \/ext  
 可选。  指定在 IDE 之外的默认 Web 浏览器中显示页。  
  
## 备注  
 **ShowWebBrowser** 命令的别名为 **navigate** 或 **nav**。  
  
## 示例  
 下面的示例在 IDE 之外的 Web 浏览器中显示 MSDN Online 主页。  如果已经打开 Web 浏览器的一个实例，则使用此实例；否则，启动新实例。  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)