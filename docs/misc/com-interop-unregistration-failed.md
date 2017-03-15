---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
当尝试注销程序集的旧副本时出现问题。  
  
 如果设置了**“为 COM 互操作 注册”**属性，则项目系统会在注册刚生成的副本之前，尝试首先注销 COM 对象的旧副本。  这样操作的目的在于保持注册表是最新的。  
  
 请参见“配置属性”文件夹中的**“生成”**属性页，以访问**“为 COM 互操作 注册”**属性。  
  
 一些可能的失败原因包括：  
  
-   无法注销程序集以前的类型库。  这可能是注册表中的权限问题。  
  
-   无法注销旧程序集。  这仍可能是注册表中的权限问题。  
  
 如果注销进程失败，可能发生 CoCreatable 对象的 GUID 泄漏，以及任何类型库 GUID 的泄漏。  但是，整个生成进程仍然会成功。  
  
## 请参阅  
 [.NET Framework 应用程序中的 COM 互操作性](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)