---
title: "IEnumCodePaths2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2"
helpviewer_keywords: 
  - "IEnumCodePaths2 接口"
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示代码路径列表。  
  
## 语法  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示代码路径列表。  
  
## 调用方的说明  
 调用 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumCodePaths2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|检索代码路径指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|跳过代码路径指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../Topic/IEnumCodePaths2::GetCount.md)|获取代码路径的数量枚举数。|  
  
## 备注  
 代码路径表示分支点或在程序函数调用。  代码路径列表表示代码执行花费的路径。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)