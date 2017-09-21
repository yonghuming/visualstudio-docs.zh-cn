---
title: "SccBeginBatch 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch 函数"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccBeginBatch 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将启动批处理序列的源代码管理操作。[SccEndBatch](../extensibility/sccendbatch-function.md) 将调用以结束该批处理。 这些批次不能嵌套。  
  
## 语法  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### 参数  
 无。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|批操作已成功开始。|  
|SCC\_E\_UNKNOWNERROR|非特定故障。|  
  
## 备注  
 源控制批处理用于跨多个项目或多个上下文中执行相同的操作。 批处理可以用于批处理操作期间消除冗余的每个项目对话框中，从用户体验。`SccBeginBatch` 函数和 [SccEndBatch](../extensibility/sccendbatch-function.md) 作为函数对用来指示开始和结束位置的操作。 不能嵌套。`SccBeginBatch` 设置一个标志，指示批处理操作正在进行。  
  
 批处理操作生效时，源代码管理插件应为用户提供最多一个对话框中的任何问题，并在所有后续操作应用来自该对话框中的响应。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)