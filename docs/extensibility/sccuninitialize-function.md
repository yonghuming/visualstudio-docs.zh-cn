---
title: "SccUninitialize 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize 函数"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUninitialize 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将清除任何分配或打开的连接创建的以前调用 [SccInitialize](../extensibility/sccinitialize-function.md) 以准备关闭源代码管理插件。  
  
## 语法  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in在中创建指向源控制插件上下文结构的指针 [SccInitialize](../extensibility/sccinitialize-function.md)。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|清理已成功完成。|  
  
## 备注  
 源代码管理插件是负责准备关闭并释放该插件为上下文结构已分配的内存。 为每个插件的给定实例一次调用的函数。 调用 [SccInitialize](../extensibility/sccinitialize-function.md) 之前此调用。 没有项目可以仍为打开状态的时间调用 `SccUninitialize`。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)