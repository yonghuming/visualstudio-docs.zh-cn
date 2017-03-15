---
title: "COM Interop registration failed | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
在注册向 COM 客户端公开功能的程序集时失败。  若发生此错误，则生成进程将会失败。  
  
 程序集可以向 COM 客户端公开对象。  项目系统提供属性以便为 COM 互操作注册公开类，生成并注册类型库以便可以从脚本语言和 Visual Basic 6 中使用这些类。  
  
 请参见**“配置属性”**文件夹中的**“生成”**属性页，以访问**“为 COM 互操作注册”**属性。  
  
 一些可能的失败原因包括：  
  
-   无法生成程序集的类型库。  这可能是磁盘空间问题或文件锁定问题，其中类型库由 Visual Studio 或某些其他进程锁定。  而且，可能未在系统上正确注册被引用程序集的类型库。  
  
-   无法注册生成的类型库。  这可能是注册表中的权限问题。  
  
-   无法注册程序集中的类。  这可能是注册表中的权限问题。  
  
 **更正此错误**  
  
-   在计算机上创建一些可用磁盘空间。  
  
-   如果有文件锁定问题，则重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   确保以管理员或具有注册表访问权限的组成员身份登录。  
  
## 请参阅  
 [.NET Framework 应用程序中的 COM 互操作性](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)