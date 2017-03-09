---
title: "如何：使用事务保存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 保存"
  - "保存数据, 使用事务"
  - "System.Transactions 命名空间"
  - "事务, 保存数据"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用事务保存数据
使用 <xref:System.Transactions> 命名空间在事务中保存数据。  使用 <xref:System.Transactions.TransactionScope> 对象来参与为您自动管理的事务。  
  
 项目不是用对 System.Transactions 程序集的引用创建的，因此您需要向使用事务的项目手动添加引用。  
  
> [!NOTE]
>  Windows 2000 和更高版本支持 <xref:System.Transactions> 命名空间。  
  
 实现事务的最简便方法是在 `using` 语句中实例化 <xref:System.Transactions.TransactionScope> 对象。  （有关更多信息，请参见 [Using 语句](/dotnet/visual-basic/language-reference/statements/using-statement) 和 [using 语句](/dotnet/csharp/language-reference/keywords/using-statement)。）`using` 语句内执行的代码将参与事务。  
  
 若要提交事务，请调用作为 using 块中最后语句的 <xref:System.Transactions.TransactionScope.Complete%2A> 方法。  
  
 若要回滚事务，请在调用 <xref:System.Transactions.TransactionScope.Complete%2A> 方法之前，引发异常。  
  
 有关更多信息，请参见 [演练：在事务中保存数据](../data-tools/save-data-in-a-transaction.md)。  
  
### 添加对 System.Transactions dll 的引用  
  
1.  从**“项目”**菜单中选择**“添加引用”**。  
  
2.  在**“.NET”**选项卡（SQL Server 项目的**“SQL Server”**选项卡）上选择**“System.Transactions”**，并单击**“确定”**。  
  
     对 System.Transactions.dll 的引用被添加到项目中。  
  
### 在事务中保存数据  
  
-   添加代码以在包含事务的 using 语句内保存数据。  下面的代码显示如何在 using 语句中创建和实例化 <xref:System.Transactions.TransactionScope> 对象：  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## 请参阅  
 [演练：在事务中保存数据](../data-tools/save-data-in-a-transaction.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)