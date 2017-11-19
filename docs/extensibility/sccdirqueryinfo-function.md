---
title: "SccDirQueryInfo 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirQueryInfo
helpviewer_keywords: SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa1bc3624c8d03cfc484aaace906c2660c3a790e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 函数
此函数将检查以了解其当前状态的完全限定目录的列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件上下文结构。  
  
 nDirs  
 [in]选择要查询的目录数。  
  
 lpDirNames  
 [in]要查询目录的完全限定路径的数组。  
  
 lpStatus  
 [在中，out]源代码管理插件为返回状态标志数组结构 (请参阅[目录状态代码](../extensibility/directory-status-code-enumerator.md)有关详细信息)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查询已成功。|  
|SCC_E_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 该函数填充返回的数组与从位的位掩码`SCC_DIRSTATUS`系列 (请参阅[目录状态代码](../extensibility/directory-status-code-enumerator.md))，对于给定的每个目录的一个条目。 该状态数组是由调用方分配的。  
  
 前一个目录重命名，以检查目录是否在源代码管理下通过查询其是否具有相应的项目，IDE 将使用此函数。 如果目录不是在源代码管理下，IDE 可以向用户提供正确的警告。  
  
> [!NOTE]
>  如果源代码管理插件选择不实现一个或多个状态的值，则未实现的位应设置为零。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [目录状态代码](../extensibility/directory-status-code-enumerator.md)