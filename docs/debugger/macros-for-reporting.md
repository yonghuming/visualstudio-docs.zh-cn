---
title: "用于报告的宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c977cd5af8714e6dc0fd07b70aba9cf7f40bfe06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="macros-for-reporting"></a>用于报告的宏
你可以使用**_RPTn**，和**_RPTFn** CRTDBG 中定义的宏。H、 要替换的使用`printf`语句进行调试。 在你的发布中自动消失这些宏生成时**_DEBUG**未定义的因此没有无需将它们括在**#ifdef**s。  
  
|宏|描述|  
|-----------|-----------------|  
|**_RPT0**， **_RPT1**， **_RPT2**， **_RPT3**， **_RPT4**|向四个自变量输出一个消息字符串和零。 对于从 _RPT1 到**_RPT4**，消息字符串作为自变量的 printf 样式格式化字符串。|  
|**_RPTF0**， **_RPTF1**， **，_RPTF2**， **_RPTF4**|与相同**_RPTn**，但这些宏还输出宏所在的位置的文件名和行号。|  
  
 请看下面的示例：  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 此代码的值输出`someVar`和`otherVar`到**stdout**。 可以使用以下对 `_RPTF2` 的调用报告同样的值另加文件名和行号：  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 如果发现某特定应用程序需要调试报告，而 C 运行库提供的宏不提供该报告，则可以编写专门设计的宏来符合您自己的需求。 在其中一个头文件，例如，你可能包括代码以下项来定义宏名**ALERT_IF2**:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 一次调用**ALERT_IF2**无法执行的所有功能**printf**本主题开头的代码：  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 因为可以方便地更改自定义宏，以便向不同目标报告或多或少的信息（取决于怎样更方便），所以该方法在调试需求不断发展时尤其有用。  
  
## <a name="see-also"></a>另请参阅  
 [CRT 调试方法](../debugger/crt-debugging-techniques.md)