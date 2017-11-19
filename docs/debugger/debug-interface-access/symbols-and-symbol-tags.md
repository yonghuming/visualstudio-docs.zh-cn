---
title: "符号和符号标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 347ea483fda44d43d73b147a41a55f0945e515e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="symbols-and-symbol-tags"></a>符号和符号标记
作为符号的使用调试接口访问 (DIA) SDK Api 可以访问程序数据库 (.pdb) 文件中存储有关已编译的程序的调试信息。 所有的符号拥有[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)和[idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)属性。 `symTag`属性指示的符号的类型由定义[SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)枚举。 `symIndexId`属性是`DWORD`包含符号的每个实例的唯一标识符的值。  
  
 符号还具有属性，可以指定有关的其他信息的符号以及对其他符号，引用最常[idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)或[idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). 当查询包含的引用的属性时，为返回的引用[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)对象。 此类属性始终成对发生，与另一个属性通过相同的名称，但后缀"id"，例如， [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)和[idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)。 中的表[符号位置](../../debugger/debug-interface-access/symbol-locations.md)，[符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)，和[符号类型的类层次结构的](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)概述的不同类型的每个属性的符号。 这些属性可能具有相关信息或对其他符号的引用。 因为`*Id`属性是只需数字序号标识符的相关属性，它们中进一步讨论将忽略。 称其为仅在需要时参数阐述。  
  
 当尝试访问该属性，如果未发生错误并且已在符号属性分配一个值，该属性的"get"方法返回`S_OK`。 返回值`S_FALSE`指示属性不是有效当前符号。  
  
## <a name="in-this-section"></a>本节内容  
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)  
 描述不同类型的符号可以具有的位置。  
  
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 介绍形成如文件、 模块和函数的词法层次结构的符号类型。  
  
 [符号类型的类层次结构](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 介绍对应不同的语言元素，如类、 数组和函数返回类型的符号类型。  
  
## <a name="see-also"></a>另请参阅  
 [调试接口访问 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)