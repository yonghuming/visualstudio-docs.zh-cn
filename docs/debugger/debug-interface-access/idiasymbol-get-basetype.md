---
title: "IDiaSymbol::get_baseType | Microsoft Docs"
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
  - "IDiaSymbol::get_baseType 方法"
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_baseType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索该符号的基础*。*  
  
## 语法  
  
```cpp#  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回从指定符号的基类型 [BasicType 枚举](../../debugger/debug-interface-access/basictype.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 符号的基本类型可以依赖于首先获得符号的类型然后询问该该基类型的返回类型。  请注意一些符号不能有一个基础类型 \(例如，结构名称。  
  
## 示例  
  
```cpp#  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [BasicType 枚举](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)