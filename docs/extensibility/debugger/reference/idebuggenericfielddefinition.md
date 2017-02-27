---
title: "IDebugGenericFieldDefinition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericFieldDefinition 接口"
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示一个字段的定义托管代码泛型类型的。  
  
## 语法  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## 方法  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|构造给定的域实例一组类型参数。|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|检索该类型为的参数的数目。|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|检索类型参数的数量与泛型字段。|  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll