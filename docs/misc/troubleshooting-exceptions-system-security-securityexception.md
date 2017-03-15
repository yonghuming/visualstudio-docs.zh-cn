---
title: "关于异常的疑难解答：System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException 类"
  - "SecurityException 类"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Security.SecurityException
当检测到一个安全错误时会引发 <xref:System.Security.SecurityException> 异常。  
  
## 相关提示  
 通过属性页调整程序集的权限级别。  
 有关详细信息，请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>。  
  
 在独立存储中存储应用程序数据。  
 独立存储是一种数据存储，它在代码与保存的数据之间定义了标准化的关联方式，从而提供隔离性和安全性。 有关详细信息，[独立存储](../Topic/Isolated%20Storage.md)。  
  
 如果使用的是 <xref:System.Windows.Forms.OpenFileDialog>，则使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法打开或保存文件。  
 这允许应用程序在部分信任情况下执行。  
  
 确保应用程序是在对本地计算机上的现有事件日志进行读写。  
 应用程序可能没有足够的权限在非本地计算机上创建日志或写入。  
  
 如果调用非托管库，则使用等效的托管库。  
 等效的 API 可能存在于 Framework 中。 有关详细信息，请参阅[互操作性疑难解答](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)。  
  
 使用安全窗口。  
 <xref:System.Security.Permissions.UIPermissionWindow> 枚举指定允许使用代码的窗口类型。  
  
 允许用户通过 <xref:System.Windows.Forms.PrintDialog> 组件进行打印。  
 这允许应用程序在部分信任情况下执行。 有关详细信息，请参阅<xref:System.Windows.Forms.PrintDialog>。  
  
 打印到默认打印机。  
 这允许应用程序在部分信任情况下执行。 您可能在尝试访问您没有访问权限的打印机。  
  
 从部署数据的同一个 Web 服务器上检索数据。  
 这允许应用程序在部分信任情况下执行。  
  
 部署 Office 解决方案时要进行检查，以确保所有必需的安全要求均已满足。  
 有关详细信息，请参阅 [Office 解决方案的特定安全注意事项](/office-dev/office-dev/specific-security-considerations-for-office-solutions)。  
  
 如果实现自定义安全对象的程序集引用了其他程序集，请将所引用的程序集添加到完全信任程序集列表中。  
 有关更多信息，请参见[Caspol.exe（代码访问安全策略工具）](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md)。  
  
## 请参阅  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)