---
title: "ADDRESS_KIND | Microsoft Docs"
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
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "ADDRESS_KIND 枚举"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定地址。  
  
## 语法  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## 术语  
 ADDRESS\_KIND\_NATIVE  
 本机地址，由 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 结构。  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 非托管地址相对 `this` \(在 Visual Basic 中`Me` \) 指针和由 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 结构。  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 非托管物理地址，由 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 结构。  
  
 ADDRESS\_KIND\_METHOD  
 类的方法，由 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 结构。  
  
 ADDRESS\_KIND\_FIELD  
 类的字段，由 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 结构。  
  
 ADDRESS\_KIND\_LOCAL  
 该地址是否为局部变量和由 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 结构表示。  
  
 ADDRESS\_KIND\_PARAM  
 方法或函数参数，由 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 结构。  
  
 ADDRESS\_KIND\_ARRAYELEM  
 数组元素，由 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 结构。  
  
 ADDRESS\_KIND\_RETVAL  
 返回值，该值表示由 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 结构。  
  
## 备注  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 方法返回包含可能的结构联合的 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构， [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构。  `DEBUG_ADDRESS_UNION` 结构的 `dwKind` 字段表示 `ADDRESS_KIND` 值并描述如何解释联合字段。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)