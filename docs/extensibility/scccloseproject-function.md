---
title: "SccCloseProject 函数 | Microsoft Docs"
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
  - "SccCloseProject"
helpviewer_keywords: 
  - "SccCloseProject 函数"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# SccCloseProject 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将关闭特定会话的结束标记的项目。  
  
## 语法  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### 参数  
 pvContext  
 源控制插件上下文结构。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|已成功关闭该项目。|  
|SCC\_E\_PROJNOTOPEN|不没有当前打开任何项目。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。|  
  
## 备注  
 [SccOpenProject](../extensibility/sccopenproject-function.md) 始终调用函数之前调用此函数。 对此函数的调用后跟在调用 `SccOpenProject` 函数或 [SccUninitialize](../extensibility/sccuninitialize-function.md), ，这完全结束与源代码管理系统的连接。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)