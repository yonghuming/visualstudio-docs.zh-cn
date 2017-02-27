---
title: "符号和符号标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "符号 [DIA SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 符号和符号标记
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试有关已编译程序的信息存储在程序数据库 \(.pdb\) 文件作为使用调试界面访问 \(DIA\) SDK API 是可访问的符号。  所有符号带有 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) 和一个 [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) 属性。  `symTag` 属性指示该符号所定义的 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 枚举。  `symIndexId` 属性是包含符号的每个实例的唯一标识符的 `DWORD` 值。  
  
 符号还可能指定有关符号的其他信息以及通常对其他符号， [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) 或 [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)的属性。  当查询包含引用的属性时，引用的形式返回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象。  此属性始终对与另一个属性被同名，但 “Id”，例如， [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) 和 [IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)作为后缀。  在 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)、 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)和 [符号类型的类层次结构](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) 轮廓的表每个的属性不同种类的符号。  这些属性可以有相关信息或对其他符号。  由于 `*Id` 属性完成它们的相关属性数字序号标识符，它们从进一步讨论省略。  它们引用仅在需要为参数声明。  
  
 当尝试访问属性，因此，如果未发生错误时，因此符号属性赋了值，属性的 “get”方法返回 `S_OK`。  `S_FALSE` 的返回值指示属性为当前符号无效。  
  
## 本节内容  
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)  
 描述符号可能具有的不同种类的位置。  
  
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 描述窗体词法层次结构 \(如文件、模块和功能的符号类型。  
  
 [符号类型的类层次结构](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 描述对应于不同的语言元素 \(如类，数组，因此，函数返回类型的符号类型。  
  
## 请参阅  
 [调试接口访问 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)