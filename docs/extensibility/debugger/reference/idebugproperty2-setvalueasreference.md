---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference 方法"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置此属性的值设置为给定的值的引用。  
  
## 语法  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### 参数  
 `rgpArgs`  
 \[in\] 通过将参数传递到托管代码的属性 setter。  如果属性 setter 不接受参数，或者此 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 对象不引用此类的属性 setter， `rgpArgs` 应是 null 值。  此参数通常是 null 值。  
  
 `dwArgCount`  
 \[in\] 参数的数目。 `rgpArgs` 数组。  
  
 `pValue`  
 \[in\] 引用，以及一 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象的形式，为要使用的值将此属性设置为。  
  
 `dwTimeout`  
 \[in\] 多长时间接受设置值，以毫秒为单位。  一个典型的值是 `INFINITE`。  这会影响所有可能的计算可能采用的时间长度。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码，通常下列操作之一:  
  
|错误|说明|  
|--------|--------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|设置从引用的值不受支持。|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|，因为此特性引用了一个方法，该值不能设置。|  
|`E_SETVALUE_VALUE_IS_READONLY`|该值是只读的，不能设置。|  
|`E_NOTIMPL`|此方法未实现。|  
  
## 请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)