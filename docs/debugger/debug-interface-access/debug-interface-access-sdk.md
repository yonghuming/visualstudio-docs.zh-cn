---
title: "调试接口访问 SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e404f0b893453fa319d5c4df97319f8e77720805
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-interface-access-sdk"></a>调试接口访问 SDK
Microsoft 调试接口访问软件开发工具包 (DIA SDK) 提供访问存储在由 Microsoft 后置编译器工具生成的程序数据库 (.pdb) 文件中的调试信息。 后置编译器工具生成的.pdb 文件的格式进行常量的修订版本，因为公开格式是不切实际的。 使用 DIA API 时，你可以开发的应用程序用于搜索和浏览存储在.pdb 文件的调试信息。 此类应用程序无法，例如，报告堆栈跟踪信息和分析性能数据。  
  
## <a name="in-this-section"></a>本节内容  
 [入门](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 将功能的概述 DIA SDK，并指定 DIA SDK 以及必需的标头和库文件的安装。  
  
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 说明了如何使用 DIA API 来查询.pdb 文件。  
  
 [符号和符号标记](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 讨论如何在 DIA API 中使用符号和符号标记。  
  
 [参考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 包含接口、 方法、 枚举和结构 DIA API。  
  
 [Dia2dump 示例](../../debugger/debug-interface-access/dia2dump-sample.md)  
 演示如何使用 DIA API 来搜索和浏览调试信息。  
  
 [Dia2dump.cpp 源文件](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 源使用代码[Dia2dump 示例](../../debugger/debug-interface-access/dia2dump-sample.md)演示 DIA API。