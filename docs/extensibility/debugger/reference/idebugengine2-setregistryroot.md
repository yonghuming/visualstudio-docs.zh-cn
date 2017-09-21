---
title: "IDebugEngine2::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置注册表支持调试引擎 \(DE\)。  
  
## 语法  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### 参数  
 `pszRegistryRoot`  
 \[in\] 使用的注册表根。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法允许 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 指定 DE 应使用获取注册表设置的备用注册表根;例如， “HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp”。  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)