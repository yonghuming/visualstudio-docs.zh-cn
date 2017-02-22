---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
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
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals 方法"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建方案中的所有局部变量的枚举数，包括编译器在内部生成的文件。  
  
## 语法  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 参数  
 `pAddress`  
 \[in\] 表示在方法中的一 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象的调试地址，指向特定范围或上下文。  
  
 `ppLocals`  
 \[out\] 返回表示任何本地的列表在指定范围的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象;否则，将不返回一个本地的 null 值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有本地。  否则，返回错误代码。  
  
## 备注  
 在包含给定的块中定义的变量只调试地址枚举。  此方法包括所有编译器生成的本地。  如果在源需要的是本地显式定义的，请调用 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 方法。  
  
 方案可包含多个范围上下文或阻止。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)