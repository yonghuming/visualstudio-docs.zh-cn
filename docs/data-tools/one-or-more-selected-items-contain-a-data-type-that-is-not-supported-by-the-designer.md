---
title: "一个或多个所选的项目包含设计器不支持的数据类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31e42bfcaf8904932d4ea864a608c943f638428c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一个或多个所选项包含设计器不支持的数据类型
一个或多个项拖动从**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]包含不支持的数据类型[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]（例如，[CLR 用户定义类型](http://msdn.microsoft.com/Library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2))。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  创建一个基于所需的表的视图，且其中不包括不支持的数据类型。  
  
2.  将从视图拖动**服务器资源管理器**/**数据库资源管理器**拖动到设计器。  
  
## <a name="see-also"></a>请参阅
[O/R 设计器消息](../data-tools/o-r-designer-messages.md)  
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)