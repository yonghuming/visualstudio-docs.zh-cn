---
title: "如何： 使用事务保存数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 23cf5ee9ef7369d8c0f52adde639adad4abe3ae6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>如何： 使用事务保存数据
将数据在事务中保存通过<xref:System.Transactions>命名空间。 使用<xref:System.Transactions.TransactionScope>对象能够参与自动为您管理的事务。  
  
项目不会对 System.Transactions 程序集的引用创建，因此你需要手动添加对使用事务的项目的引用。  
  
实现事务的最简单方法是实例化<xref:System.Transactions.TransactionScope>对象在`using`语句。 (有关详细信息，请参阅[Using 语句](/dotnet/visual-basic/language-reference/statements/using-statement)，和[using 语句](/dotnet/csharp/language-reference/keywords/using-statement)。)运行中的代码`using`语句参与该事务。  
  
若要提交事务，调用<xref:System.Transactions.TransactionScope.Complete%2A>作为中使用的最后一个语句的方法阻止。  
  
若要回滚事务，应引发异常之前调用<xref:System.Transactions.TransactionScope.Complete%2A>方法。  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>若要添加对 System.Transactions.dll 的引用  
  
1.  上**项目**菜单上，选择**添加引用**。  
  
2.  上**.NET**选项卡 (**SQL Server**对于 SQL Server 项目的选项卡)，选择**System.Transactions**，然后选择**确定**。  
  
     System.Transactions.dll 的引用添加到项目。  
  
## <a name="to-save-data-in-a-transaction"></a>若要将数据保存在事务中  
  
-   添加代码以保存在中使用的数据包含事务的语句。 下面的代码演示如何创建和实例化<xref:System.Transactions.TransactionScope>对象在 using 语句：  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>请参阅
[将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)  
[演练： 将数据保存在事务中](../data-tools/save-data-in-a-transaction.md)  