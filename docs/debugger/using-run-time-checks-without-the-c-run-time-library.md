---
title: "使用无 C 运行库运行时检查 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4cef71a9e9557b5a12a7dfe857d67b22dc69b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>使用无 C 运行库的运行时检查
如果链接程序而不 C 运行时库，使用**/NODEFAULTLIB**，并想要使用运行时检查，则必须链接 runtmchk.lib。  
  
 `_RTC_Initialize` 为运行时检查初始化程序。 如果未链接 C 运行库，必须在调用 `_RTC_Initialize` 之前检查是否用运行时错误检查编译了程序：  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 如果不链接 C 运行库，还必须定义一个称为 `_CRT_RTC_INITW` 的函数。 `_CRT_RTC_INITW` 将用户定义的函数安装为默认的错误报告函数，如下所示：  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 安装了默认错误报告函数后，可以使用 `_RTC_SetErrorFuncW` 安装附加错误报告函数。 有关详细信息，请参阅[_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)。  
  
## <a name="see-also"></a>另请参阅  
 [如何：使用本机运行时检查](../debugger/how-to-use-native-run-time-checks.md)