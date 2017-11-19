---
title: "概述 （调试接口访问 SDK） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cd0206e402600cbe9002c931adb7ff6a2cc680
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="overview-debug-interface-access-sdk"></a>概述（调试接口访问 SDK）
DIA SDK 用于访问 Microsoft 调试信息。 DIA SDK 提供对基于 COM 的无需重写代码，当 Microsoft 发生更改时的调试信息的格式的 API 集。 DIA SDK 还可以从选定的一组以前版本的调试信息，位于由生成的.pdb 和.dbg 文件读取[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]5.0 及更高版本。  
  
 DIA SDK 中的每个接口表示不同的 COM 对象，除外，其中有其他声明。 其他接口，因此其他对象，创建通过显式查询，如[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)或[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是通过调用`QueryInterface`上现有的接口指针。  
  
## <a name="see-also"></a>另请参阅  
 [Idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)