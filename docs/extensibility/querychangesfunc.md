---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "QUERYCHANGESFUNC 回调函数"
  - "QUERYCHANGESDATA 结构"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

这是由一个回调函数 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 操作，以枚举集合的文件的名称并确定每个文件的状态。  
  
 `SccQueryChanges` 函数提供一组文件和一个指向 `QUERYCHANGESFUNC` 回调。 源代码管理插件枚举给定的列表，并提供相应的每个文件在列表中的状态 \(通过此回调\)。  
  
## 签名  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## 参数  
 pvCallerData  
 \[\] in `pvCallerData` 参数由呼叫方 \(IDE\) 传递给 [SccQueryChanges](../extensibility/sccquerychanges-function.md)。 源代码管理插件应当作出任何假设内容的此值。  
  
 pChangesData  
 \[\] in指向 [QUERYCHANGESDATA 结构](#LinkQUERYCHANGESDATA) 结构的结构描述对文件的更改。  
  
## 返回值  
 IDE 将返回相应的错误代码:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|继续进行处理。|  
|SCC\_I\_OPERATIONCANCELED|停止处理。|  
|SCC\_E\_xxx|任何相应的 SCC 错误应停止处理。|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 结构  
 为每个文件中传递的结构如下所示:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 此结构 \(以字节为单位\) 的大小。  
  
 lpFileName  
 此项的原始文件名称。  
  
 dwChangeType  
 指示文件的状态代码:  
  
|代码|说明|  
|--------|--------|  
|`SCC_CHANGE_UNKNOWN`|无法通知发生了什么变化。|  
|`SCC_CHANGE_UNCHANGED`|此文件未名称更改。|  
|`SCC_CHANGE_DIFFERENT`|文件使用不同的标识，但数据库中存在相同的名称。|  
|`SCC_CHANGE_NONEXISTENT`|在数据库中或本地文件不存在。|  
|`SCC_CHANGE_DATABASE_DELETED`|从数据库中删除的文件。|  
|`SCC_CHANGE_LOCAL_DELETED`|删除本地文件，但该文件仍在数据库中。 如果无法确定该名称，返回 `SCC_CHANGE_DATABASE_ADDED`。|  
|`SCC_CHANGE_DATABASE_ADDED`|文件添加到数据库，但本地不存在。|  
|`SCC_CHANGE_LOCAL_ADDED`|文件数据库中不存在，并且是新的本地文件。|  
|`SCC_CHANGE_RENAMED_TO`|重命名或移动的数据库中文件 `lpLatestName`。|  
|`SCC_CHANGE_RENAMED_FROM`|重命名或移动的数据库中文件 `lpLatestName`; 如果这是开销太大而跟踪时，返回不同的标记，如 `SCC_CHANGE_DATABASE_ADDED`。|  
  
 lpLatestName  
 此项目的当前的文件名称。  
  
## 请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [错误代码](../extensibility/error-codes.md)