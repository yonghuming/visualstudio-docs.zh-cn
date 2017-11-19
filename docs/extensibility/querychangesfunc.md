---
title: "QUERYCHANGESFUNC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2da455cdafc399b64fe42109c7973185ce69c79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
这是由一个回调函数[SccQueryChanges](../extensibility/sccquerychanges-function.md)操作枚举文件名称的集合，并确定每个文件的状态。  
  
 `SccQueryChanges`函数提供的文件和指向的指针列表`QUERYCHANGESFUNC`回调。 源代码管理插件枚举给定的列表，并为每个列表中的文件提供 （通过此回调中） 的状态。  
  
## <a name="signature"></a>签名  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>参数  
 pvCallerData  
 [in]`pvCallerData`参数由调用方 (IDE) 传递给[SccQueryChanges](../extensibility/sccquerychanges-function.md)。 源代码管理插件应作出任何假设内容的此值。  
  
 pChangesData  
 [in]指向[QUERYCHANGESDATA 结构](#LinkQUERYCHANGESDATA)结构描述的文件更改。  
  
## <a name="return-value"></a>返回值  
 IDE 返回相应的错误代码：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|继续进行处理。|  
|SCC_I_OPERATIONCANCELED|停止处理。|  
|SCC_E_xxx|任何相应的 SCC 错误应停止处理。|  
  
##  <a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA 结构  
 每个文件中传递的结构如下所示：  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 此结构 （以字节为单位） 的大小。  
  
 lpFileName  
 此项的原始文件名称。  
  
 dwChangeType  
 指示文件的状态代码：  
  
|代码|描述|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|无法告知发生了什么变化。|  
|`SCC_CHANGE_UNCHANGED`|没有此文件的名称更改。|  
|`SCC_CHANGE_DIFFERENT`|文件使用不同的标识，但数据库中存在相同的名称。|  
|`SCC_CHANGE_NONEXISTENT`|在数据库中或本地文件不存在。|  
|`SCC_CHANGE_DATABASE_DELETED`|从数据库中删除的文件。|  
|`SCC_CHANGE_LOCAL_DELETED`|在本地删除的文件，但该文件仍存在数据库中。 如果无法确定该名称，则返回`SCC_CHANGE_DATABASE_ADDED`。|  
|`SCC_CHANGE_DATABASE_ADDED`|文件添加到数据库，但不存在本地。|  
|`SCC_CHANGE_LOCAL_ADDED`|文件数据库中不存在，且是一个新的本地文件。|  
|`SCC_CHANGE_RENAMED_TO`|文件重命名或移动在与数据库中`lpLatestName`。|  
|`SCC_CHANGE_RENAMED_FROM`|文件重命名或从数据库中移动`lpLatestName`; 如果这是过于昂贵，若要跟踪，返回一个不同的标志，例如`SCC_CHANGE_DATABASE_ADDED`。|  
  
 lpLatestName  
 此项的当前文件名称。  
  
## <a name="see-also"></a>另请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [错误代码](../extensibility/error-codes.md)