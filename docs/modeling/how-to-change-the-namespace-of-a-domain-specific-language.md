---
title: "如何：更改域特定语言的命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 命名空间"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# 如何：更改域特定语言的命名空间
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以更改域特定语言 \(dsl\) 的命名空间。  您必须进行在 **DSL 资源管理器**，在 DSL 包项目的属性以及程序集信息。  
  
### 更改域特定语言 \(dsl\) 的命名空间  
  
1.  在 **DSL 资源管理器**，单击 **DSL** 节点。  
  
2.  在 **属性** 窗口中，更改 **命名空间** 属性。  
  
3.  保存解决方案和转换模板。  
  
4.  在 **项目** 菜单上，单击 **DSL 属性**。  
  
     此时将显示该项目的属性  
  
5.  单击**“应用程序”**选项卡。  
  
6.  更改 **默认命名空间** 属性设置为新命名空间名称。  
  
7.  如果您要更改程序集的名称，请更改 **程序集名称属性。**  
  
8.  如果更改了程序集名称，请打开 DslPackage \\Package .tt 和更新以下行:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. 如果您编写了任何自定义代码，请确保更改命名空间，而类在代码文件中引用。  
  
10. 重置 Visual Studio 的实验实例。  
  
    1.  删除 **\\Users\\***{名称}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  在窗口 **开始** 菜单中，选择 **所有程序**， **Microsoft Visual Studio 2010 SDK**， **工具**， **重置的实验实例**。  
  
11. 在 **生成** 菜单中，选择 **重新生成解决方案**。  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)