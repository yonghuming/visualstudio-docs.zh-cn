---
title: "SccEnumChangedFiles 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccEnumChangedFiles
helpviewer_keywords: SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad62f14ea658e4af6e22d4beef410e6d9cf02df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 函数
给定的本地文件的列表，此函数将确定哪些文件是不同于在源代码控制数据库中的相应版本。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 cFiles  
 [in]中指定的文件名称的数`lpFileNames`数组。 此外指定大小的`plIsFileDifferent`数组。  
  
 lpFileNames  
 [in]要检查的本地文件名称的数组。  
  
 plIsFileDifferent  
 [在中，out]值，该值指示每个文件的差异状态数组 (数组必须至少具有`cFiles`条目)。 该文件是不同的非零种方式。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|操作已成功完成。|  
|SCC_UNSPECIFIEDERROR|一般性错误。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)