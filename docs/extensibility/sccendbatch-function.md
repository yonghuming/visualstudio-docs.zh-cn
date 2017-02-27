---
title: "SccEndBatch 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch 函数"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccEndBatch 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数最后一批的源代码管理操作。 这些批次不能嵌套。  
  
## 语法  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### 参数  
 无。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|批操作成功的结论。|  
|SCC\_E\_UNKNOWNERROR|非特定故障。|  
  
## 备注  
 源控件批处理用于跨多个项目或多个上下文中执行相同的源代码管理操作。 批处理可以用于批处理操作期间消除冗余的对话框中，从用户体验。[SccBeginBatch](../extensibility/sccbeginbatch-function.md) 和 `SccEndBatch` 函数用作一对，以指示的开头和结尾的操作。 不能嵌套。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)