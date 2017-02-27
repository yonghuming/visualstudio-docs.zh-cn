---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_LOCAL 结构"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示一个局部变量的地址在范围内的 \(通常是函数或方法\)。  
  
## 语法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## 术语  
 tokMethod  
 方法的 ID 或函数局部变量是的一部分。  
  
 \[c\+\+\] `_mdToken` 是 32 位 `int`的 `typedef` 。  
  
 pLocal  
 地址此结构表示的标记。  
  
 dwIndex  
 可以是此局部变量索引在方法或函数，或某些其他值 \(特定语言\)。  
  
## 备注  
 此结构是联合的一部分。 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构时， `DEBUG_ADDRESS_UNION` 结构的 `dwKind` 字段设置为 `ADDRESS_KIND_LOCAL` 时 \(从 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举的值\)。  
  
 只有 C\+\+`Warning:`\[\]，如果 `pLocal` 不为空，则必须对标记指针的 `Release` \(`addr` 是在 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构的字段\):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)