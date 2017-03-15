---
title: "LocationType | Microsoft Docs"
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
  - "LocationType 枚举"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指示在符号位置信息包含的。  
  
## 语法  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Elements  
 `LocIsNull`  
 单元格信息不可用。  
  
 `LocIsStatic`  
 位置是静态的。  
  
 `LocIsTLS`  
 位置在线程本地存储。  
  
 `LocIsRegRel`  
 placement 为注册相关。  
  
 `LocIsThisRel`  
 placement 为 `this`\- 相对。  
  
 `LocIsEnregistered`  
 位置在注册。  
  
 `LocIsBitField`  
 位置。位域。  
  
 `LocIsSlot`  
 placement 为 Microsoft 中间语言 \(msil\) 槽。  
  
 `LocIsIlRel`  
 placement 为 MSIL 相对的。  
  
 `LocInMetaData`  
 位置在元数据。  
  
 `LocIsConstant`  
 位置按一个常数值。  
  
 `LocTypeMax`  
 位置的数字输入此枚举。  
  
## 备注  
 属性可用于 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 接口依赖于图像文件中的符号的位置。  有关更多信息，请参见 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)。  
  
 此枚举的值通过对 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md) 方法的调用返回。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)