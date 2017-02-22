---
title: "SccGetVersion 函数 | Microsoft Docs"
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
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion 函数"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetVersion 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数获取受源代码管理插件源控制插件 API 的版本号。  
  
## 语法  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### 参数  
 无。  
  
## 返回值  
 一个 `LONG` 数据类型，包含受支持的源控制插件 API 的版本号:  
  
|WORD|描述|  
|----------|--------|  
|HIWORD|主要版本|  
|LOWORD|次要版本|  
  
## 备注  
 例如，如果源代码管理插件支持的源控制插件 API 1.3 版，此函数将返回 0x0103。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)