---
title: "报表挂钩函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport 函数"
  - "_CrtSetReportHook 函数"
  - "调试器, 报表挂钩函数"
  - "调试 [C++], 挂钩函数"
  - "挂钩, 报表"
  - "内存分配, 调试堆"
  - "报表挂钩函数"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 报表挂钩函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

每次 [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) 生成调试报告时都会调用报告挂钩函数（使用 [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook) 安装）。  可以使用报告挂钩函数以及其他项筛选报告以集中于特定类型的分配。  报告挂钩函数应具有如下原型：  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 传递给 **\_CrtSetReportHook** 的指针为 **\_CRT\_REPORT\_HOOK** 类型，如 CRTDBG.H 中所定义：  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 当运行库调用您的挂钩函数时，*nRptType* 参数包含报告类别（**\_CRT\_WARN**、**\_CRT\_ERROR** 或 **\_CRT\_ASSERT**），*szMsg* 包含指向完全汇编的报告消息字符串的指针，而 *retVal* 指定 `_CrtDbgReport` 应在生成报告以后继续正常执行还是启动调试器。（*retVal* 值为零继续执行，值为 1 启动调试器。）  
  
 如果挂钩完全处理了所讨论的消息，因而不需要进一步的报告，那么应返回 **TRUE**。  如果返回 **FALSE**，`_CrtDbgReport` 将以正常方式报告消息。  
  
## 请参阅  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/zh-cn/21e1346a-6a17-4f57-b275-c76813089167)