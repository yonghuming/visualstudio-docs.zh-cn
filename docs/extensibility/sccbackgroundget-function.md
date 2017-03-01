---
title: "SccBackgroundGet 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8bc845c2ef3cb4ece3e52dca272fdc75208e8dbd
ms.lasthandoff: 02/22/2017

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
 [in]源控制插件上下文指针。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [in、 out]要检索的文件的名称的数组。  
  
> [!NOTE]
>  名称必须是完全限定的本地文件名。  
  
 dwFlags  
 [in]命令标志 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 dwBackgroundOperationID  
 [in]与此操作关联的唯一值。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回下列值之一︰  
  
|值|说明|  
|-----------|-----------------|  
|SCC_OK|操作已成功完成。|  
|SCC_E_BACKGROUNDGETINPROGRESS|背景检索正在的进行 （源代码管理插件应返回此仅当它不支持同时执行的批操作）。|  
|SCC_I_OPERATIONCANCELED|正在完成前已取消操作。|  
  
## <a name="remarks"></a>备注  
 始终在与加载的源代码管理插件的不同线程上调用此函数。 此函数不应返回之前完成;但是，它可以多次调用与多个文件 （全部在同一时间） 的列表。  
  
 使用`dwFlags`参数等同于[SccGet](../extensibility/sccget-function.md)。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
