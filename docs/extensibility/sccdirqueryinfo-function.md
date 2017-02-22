---
title: "SccDirQueryInfo 函数 | Microsoft Docs"
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
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo 函数"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccDirQueryInfo 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将检查以了解其当前状态的完全限定目录的列表。  
  
## 语法  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文结构。  
  
 nDirs  
 \[\] in选择要查询的目录数。  
  
 lpDirNames  
 \[\] in若要查询目录的完全限定路径的数组。  
  
 lpStatus  
 \[in、 out\]源代码管理插件返回的状态标志的数组结构 \(请参阅 [目录状态代码](../extensibility/directory-status-code-enumerator.md) 有关的详细信息\)。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|查询已成功。|  
|SCC\_E\_OPNOTSUPPORTED|源代码控制系统不支持此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定故障。|  
  
## 备注  
 函数填充返回数组中的位的位掩码与 `SCC_DIRSTATUS` 系列 \(请参阅 [目录状态代码](../extensibility/directory-status-code-enumerator.md)\)，为给定每个目录中的一个条目。 由调用方分配状态数组。  
  
 IDE 将使用此函数之前重命名目录检查目录是否在源代码管理下通过查询其是否具有相应的项目。 如果目录不是源代码管理下，IDE 可以向用户提供正确的警告。  
  
> [!NOTE]
>  如果源代码管理插件选择不实现一个或多个状态的值，则未实现的位应设置为零。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [目录状态代码](../extensibility/directory-status-code-enumerator.md)