---
title: "IDebugModule2::GetInfo | Microsoft Docs"
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
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "GetInfo 方法"
  - "IDebugModule2::GetInfo 方法"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取有关此模块的信息。  
  
## 语法  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### 参数  
 `dwFields`  
 \[in\] 指定标志的组合。 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 枚举的 `pInfo` 的哪些字段将完成。  
  
 `pInfo`  
 \[in, out\] 在模块的声明填充的 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 结构包含在 **模块** 窗口中显示模块的名称。  
  
## 请参阅  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)