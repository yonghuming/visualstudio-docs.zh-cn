---
title: "Web 控件库（托管代码） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "调试 [Visual Studio], Web 控件库"
  - "调试 DLL"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Web 控件库（托管代码）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Web 控件库项目模板创建 DLL。  因为类库是 DLL，所以不能直接运行它。  必须创建嵌入该控件的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 页。  有关详细信息，请参阅 [Web Control Library Template](http://msdn.microsoft.com/zh-cn/00666b07-71d2-4ace-a13c-cc130a3ce372)。  
  
### 调试 Web 控件库（方法 1）  
  
1.  打开一个现有的 Web 控件库项目，或者新建一个项目。  
  
2.  创建嵌入该控件的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 页。  
  
3.  在承载 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 测试套的网站上，创建名为 `/Code` 的子目录。  
  
4.  将该控件的源代码复制到 `/Code` 子目录中。  
  
5.  打开 `/Code` 子目录下的源代码并设置断点。  
  
6.  打开浏览器窗口，将 URL 指向该测试套。  控件中的断点将被命中，您可以开始调试。  
  
### 调试 Web 控件库（方法 2）  
  
1.  创建宿主应用程序项目，并在同一解决方案中创建 Web 控件项目。  
  
2.  在**“解决方案资源管理器”**中右击宿主应用程序，然后选择**“添加引用”**。  
  
3.  向该 Web 控件项目添加引用。  
  
## 请参阅  
 [ASP.NET Web 应用程序](../debugger/debugging-preparation-aspnet-web-applications.md)