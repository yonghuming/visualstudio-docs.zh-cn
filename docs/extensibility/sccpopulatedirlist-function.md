---
title: "SccPopulateDirList 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateDirList
helpviewer_keywords: SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec22eaeaf24af1c65823c64c65dd2c39f1003ec8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函数
此函数将确定哪些目录和 （可选） 使用文件存储在源代码管理，提供要检查的目录列表中。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 nDirs  
 [in]目录中的路径数`lpDirPaths`数组。  
  
 lpDirPaths  
 [in]若要检查的目录路径的数组。  
  
 pfnPopulate  
 [in]要为每个目录路径和 （可选） 中的文件名调用的回调函数`lpDirPaths`(请参阅[POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)有关详细信息)。  
  
 pvCallerData  
 [in]要传递的值未更改对回调函数。  
  
 fOptions  
 [in]控制如何处理目录的值的组合 (请参阅的"PopulateDirList 标志"部分[Bitflags 使用特定命令](../extensibility/bitflags-used-by-specific-commands.md)有关可能的值)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功完成该操作。|  
|SCC_E_UNKNOWNERROR|出现了错误。|  
  
## <a name="remarks"></a>备注  
 只有那些目录和 （可选） 在源控件存储库中的文件名称传递给回调函数。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags 由特定的命令](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [错误代码](../extensibility/error-codes.md)