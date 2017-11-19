---
title: "SccAddFilesFromSCC 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFilesFromSCC
helpviewer_keywords: SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1764bfc503e25860326b1910c432edcf95c8f21c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 函数
此函数将从源代码管理文件的列表添加到当前打开的项目中。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpUser  
 [在中，out]（最多 SCC_USER_SIZE，包括 null 结束符) 用户名。  
  
 lpAuxProjPath  
 [在中，out]标识项目的辅助字符串 (最多`SCC_PRJPATH_`大小，包括 null 终止符)。  
  
 cFiles  
 [in]通过给定的文件数`lpFilePaths`。  
  
 lpFilePaths  
 [在中，out]要添加到当前项目的文件名的数组。  
  
 lpDestination  
 [in]从中对文件进行写入目标路径。  
  
 lpComment  
 [in]要应用于每个正在添加的文件的注释。  
  
 pbResults  
 [在中，out]数组的标志设置为指示成功 （零或不为 TRUE） 或失败 （0 或 FALSE） 为每个文件 (数组的大小必须至少`cFiles`长)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|项目未打开。|  
|SCC_E_OPNOTPERFORMED|连接不是连接到与指定的相同的项目`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|用户无权更新数据库。|  
|SCC_E_NONSPECIFICERROR|未知的错误。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)