---
title: "错误： SQL 可以 &#39; 是找不到 SSDEBUGPS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>错误： SQL 可以 &#39; 是找不到 SSDEBUGPS
SSDEBUGPS.dll 为 SQL Server Debugging Host 组件。  
  
 此错误在尝试开始调试时发生，指示指定的文件在 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 计算机上不存在。 可能的原因是从未运行远程调试安装，或是由于某种原因删除了此文件。  
  
 若要解决此错误的两种方式： 通过重新运行远程调试安装程序，并通过复制文件放到[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。  
  
 若要重新运行远程调试安装程序，请按照说明[远程调试](../debugger/remote-debugging.md)。  
  
 如果可以找到 ssdebugps.dll 的某个副本，你可以将其复制到[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。 如果存在，该文件会位于目录 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 中。 你可能会发现它在另一台[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]具有计算机上的计算机，或[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]安装。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>将 SSDEBUGPS.dll 复制到 SQL Server 2005 计算机上  
  
1.  上的文件复制到具有相同名称和路径的目录[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]机。  
  
2.  注册通过打开**命令提示符**，并运行以下命令：  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```