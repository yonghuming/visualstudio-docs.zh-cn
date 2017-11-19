---
title: "符号类型的词法层次结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0077ababbbcfb1b2dff77a8847f5e0e0671241be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="lexical-hierarchy-of-symbol-types"></a>符号类型的词法层次结构
下表显示词法层次结构中的符号类型。  
  
## <a name="symbol-types"></a>符号类型  
  
|符号类型|描述|  
|-----------------|-----------------|  
|[批注](../../debugger/debug-interface-access/annotation.md)|指定在程序代码中的带批注的位置。|  
|[块](../../debugger/debug-interface-access/block.md)|在函数中指定嵌套的作用域。|  
|`Compiland`|指定`compiland`链接到的.exe 文件。|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|指定编译单位数据可能需要加载其他编译单位的详细信息，并因此会产生开销运行时检索。|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|指定重要到编译单位编译任何其他环境变量。|  
|[自定义（调试接口访问 SDK）](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|指定的用户定义符号。|  
|[数据（调试界面访问 SDK）](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|指定为参数、 局部变量、 全局变量和类成员的此类变量。|  
|[Exe](../../debugger/debug-interface-access/exe.md)|指定数据; 全局作用的域对应于整个.exe 或.dll 文件。|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|指定的函数中有一个定义的点处的调试是结束。|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|指定具有定义的点的函数的调试在即将开始。|  
|[函数（调试接口访问 SDK）](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|指定的函数。|  
|[标签（调试接口访问 SDK）](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|在程序代码中指定的位置。|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|指定生成可执行程序时，将显示外部符号。|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|指定`thunk`。|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|指定`namespace`标识符。|  
  
> [!NOTE]
>  其他符号属性可根据符号类型。 中的各个符号主题列出了这些属性。  
  
## <a name="see-also"></a>另请参阅  
 [符号类型的类层次结构](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [符号和符号标记](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)