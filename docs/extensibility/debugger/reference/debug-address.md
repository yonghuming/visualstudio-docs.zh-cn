---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "DEBUG_ADDRESS 结构"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示地址。  
  
## 语法  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## 术语  
 ulAppDomainID  
 进程 ID.  
  
 guidModule  
 包含此地址模块的 GUID。  
  
 tokClass  
 标识此地址的类或类型标记。  
  
> [!NOTE]
>  除了为类类型的，一个标识符。此值是特定于符号提供程序并没有一般意义。  
  
 地址  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构，结构包含联合描述各个地址类型。  值 `addr`。`dwKind` 来自 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举，说明如何解释联合。  
  
## 备注  
 此结构传递给将填充的 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 方法。  
  
 **警告 \[只有 C\+\+\]**  
  
 如果 `addr.dwKind` 是 `ADDRESS_KIND_METADATA_LOCAL` ，并且，如果 `addr.addr.addrLocal.pLocal` 不是 null 值，则必须对标记指针的 `Release` :  
  
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
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)