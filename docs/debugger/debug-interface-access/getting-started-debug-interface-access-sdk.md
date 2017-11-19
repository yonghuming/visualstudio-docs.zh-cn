---
title: "入门 （调试接口访问 SDK） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 938aaf760a2a6305580331945875391e6ad819af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-debug-interface-access-sdk"></a>入门（调试接口访问 SDK）
调试接口访问 (DIA) SDK 向你提供指导文档和示例，说明了如何使用 DIA API。 使用的接口和方法在 DIA SDK 开发自定义应用程序打开的.pdb 和.dbg 文件并搜索其内容实现符号、 值、 属性、 地址和其他调试信息。 此 SDK 还提供了与在 c + + 应用程序中找到的符号关联的属性引用表。  
  
 若要充分利用 DIA SDK，你应熟悉以下：  
  
-   C + + 编程语言  
  
-   COM 编程  
  
-   用于编译示例 visual Studio 集成的开发环境 (IDE)  
  
 使用 Visual Studio 通常安装 DIA SDK，其默认位置是*[驱动器]*files\microsoft Visual Studio 9.0\DIA SDK。 作为安装的一部分，msdia90.dll，实现 DIA SDK，将自动注册，因此你需要要做，以使用它的所有是包括`dia2.h`程序和链接中`diaguids.lib`。  
  
 标头： include\dia2.h  
  
 库： lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>本节内容  
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 查看 DIA.的基本体系结构  
  
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 有关如何使用 DIA API 来查询.pdb 文件提供分步说明。  
  
## <a name="see-also"></a>另请参阅  
 [调试接口访问 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)