---
title: "SccGetEvents 函数 | Microsoft Docs"
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
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents 函数"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetEvents 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可检索已排队的状态事件。  
  
## 语法  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 lpFileName  
 \[in、 out\]源代码管理插件放置 \(最多 \_MAX\_PATH 字符为单位\) 返回的文件名的位置的缓冲区。  
  
 lpStatus  
 \[in、 out\]将返回状态代码 \(请参阅 [文件状态代码](../extensibility/file-status-code-enumerator.md) 有关可能的值\)。  
  
 pnEventsRemaining  
 \[in、 out\]返回保留在队列中进行此调用后的条目数。 如果此数量很大，可能会决定调用方调用 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 以获取所有相关信息一次。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|获取成功的事件。|  
|SCC\_E\_OPNOTSUPPORTED|不支持此功能。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。|  
  
## 备注  
 空闲处理，以查看是否已在源代码管理下的文件的任何状态更新过程中调用此函数。 源代码管理插件维护它知道的所有文件的状态，并每次更改状态进行了说明该插件的状态和关联的文件存储在队列中。 当 `SccGetEvents` 调用时，顶部检索队列中的元素并将其返回。 此函数被约束为返回唯一以前缓存的信息，并且必须具有非常快速的周转 \(也就是说，任何读取磁盘的或询问源代码管理系统状态\);否则，IDE 的性能可能开始下降。  
  
 如果不没有报告任何状态更新，源代码管理插件会将空字符串存储在所指向的缓冲区 `lpFileName`。 否则，该插件将存储该文件的完整路径名称为该状态信息已更改，并返回相应的状态代码 \(中详述的值之一 [文件状态代码](../extensibility/file-status-code-enumerator.md)\)。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)