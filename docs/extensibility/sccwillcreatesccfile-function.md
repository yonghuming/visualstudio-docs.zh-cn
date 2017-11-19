---
title: "SccWillCreateSccFile 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccWillCreateSccFile
helpviewer_keywords: SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b6aa6ead6811f50cc186f46561b214ba4cd0905
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函数
此函数可确定源代码管理插件是否支持 MSSCCPRJ 创建。每个给定文件 SCC 文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件的上下文指针。  
  
 nFiles  
 [in]文件名称中包含的数量`lpFileNames`数组的长度以及`pbSccFiles`数组。  
  
 lpFileNames  
 [in]若要检查的完全限定的文件名称的数组 （数组必须由调用方已分配）。  
  
 pbSccFiles  
 [在中，out]要在其中存储结果的数组。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_INVALIDFILEPATH|其中一个数组中的路径无效。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 使用的文件，以确定如果源代码管理插件在中提供支持 MSSCCPRJ 列表调用此函数。SCC 文件为每个给定文件 （针对 MSSCCPRJ 的详细信息。SCC 文件，请参阅[MSSCCPRJ。SCC 文件](../extensibility/mssccprj-scc-file.md))。 源控件插件可以声明它们是否具有创建 MSSCCPRJ 的功能。通过声明的 SCC 文件`SCC_CAP_SCCFILE`在初始化过程。 插件返回`TRUE`或`FALSE`在每个文件`pbSccFiles`数组以指示哪些给定文件具有 MSSCCPRJ。SCC 支持。 如果该插件从函数返回成功代码，将遵循返回数组中的值。 在失败时，该数组将被忽略。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ.SCC 文件](../extensibility/mssccprj-scc-file.md)