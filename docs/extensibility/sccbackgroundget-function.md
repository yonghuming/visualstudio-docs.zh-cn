---
title: "SccBackgroundGet 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBackgroundGet
helpviewer_keywords: SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85b700f0cb1e3a364cae69ff6c628151ea6a7bd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 函数
此函数可检索从源代码管理每个指定的文件的无用户干预。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [在中，out]要检索的文件名称的数组。  
  
> [!NOTE]
>  这些名称必须是完全限定的本地文件名。  
  
 dwFlags  
 [in]命令标志 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 dwBackgroundOperationID  
 [in]与此操作关联的唯一值。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|操作已成功完成。|  
|SCC_E_BACKGROUNDGETINPROGRESS|后台检索已正在的进行 （源代码管理插件应返回此仅当它不支持同时执行的批操作）。|  
|SCC_I_OPERATIONCANCELED|正在完成前已取消操作。|  
  
## <a name="remarks"></a>备注  
 始终在不同于加载源代码管理插件线程上调用此函数。 此函数不应返回直到完成;但是，它可以多次调用与多个文件，会全部在同一时间的列表。  
  
 使用`dwFlags`自变量是相同[SccGet](../extensibility/sccget-function.md)。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)