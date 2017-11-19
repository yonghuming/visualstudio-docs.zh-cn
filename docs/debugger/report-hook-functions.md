---
title: "报告挂钩函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51fd8ce8618dfa7b3e8adcc7326c57905d325999
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="report-hook-functions"></a>报表挂钩函数
报告挂钩函数，使用安装[_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook)，每次调用[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)生成调试报告。 可以使用报告挂钩函数以及其他项筛选报告以集中于特定类型的分配。 报告挂钩函数应具有如下原型：  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 指针传递给**_CrtSetReportHook**属于类型**_CRT_REPORT_HOOK**，如 CRTDBG 中定义。H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 当运行时库调用您的挂钩函数， *nRptType*自变量包含报表的类别 (**_CRT_WARN**， **_CRT_ERROR**，或**_CRT_ASSERT**)， *szMsg*包含指向完全装配的报表消息字符串，和*retVal*指定是否`_CrtDbgReport`应继续正常执行后生成的报表或启动调试器。 (A *retVal*值为零继续执行，值为 1 启动调试器。)  
  
 如果挂钩完全处理了所涉及的消息，以便不执行进一步的报告要求，它应返回**TRUE**。 如果它返回**FALSE**，`_CrtDbgReport`通常将报告消息。  
  
## <a name="see-also"></a>另请参阅  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 示例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)