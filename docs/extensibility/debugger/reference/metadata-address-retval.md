---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_RETVAL 结构"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示从方法或函数返回的值。  
  
## 语法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## 术语  
 tokMethod  
 此返回值是为该方法的 ID。  
  
 dwCorType  
 返回值的基类型。 这是一个介于 `CorElementType` 枚举中定义 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK corhdr.h 中的文件。  
  
 dwSigSize  
 返回值签名的大小 \(存储在 `rgSig`\)。  
  
 rgSig  
 形成的返回值的签名的字节数组。  
  
## 备注  
 此结构是中的联合的一部分 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构时 `dwKind` 字段 `DEBUG_ADDRESS_UNION` 结构设置为 `ADDRESS_KIND_RETVAL` \(取值范围为 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举\)。  
  
## 要求  
 标头 ︰ sh.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)