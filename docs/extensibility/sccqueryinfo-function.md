---
title: "SccQueryInfo 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 4efd9b29a89bc490255c35558e5862ebc14b7fec
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函数
此函数可获取一组在源代码管理下的所选文件的状态信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组和长度`lpStatus`数组。  
  
 lpFileNames  
 [in]要查询的文件的名称的数组。  
  
 lpStatus  
 [在中，out]在源代码管理插件用于返回每个文件的状态标志数组。 有关详细信息，请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查询已成功。|  
|SCC_E_ACCESSFAILURE|时访问网络或争用问题引起的可能的源控制系统出现问题。 建议重试。|  
|SCC_E_PROJNOTOPEN|项目不是受源代码管理打开的。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 如果`lpFileName`为空字符串，当前没有要更新的状态信息。 否则，很可能已更改的状态信息的文件的完整路径名称。  
  
 返回的数组可以是一个位屏蔽的`SCC_STATUS_xxxx`bits。 有关详细信息，请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)。 源代码管理系统可能不支持所有位类型。 例如，如果`SCC_STATUS_OUTOFDATE`未提供，则只是未设置位。  
  
 在使用此函数来签出文件，请注意以下`MSSCCI`状态要求：  
  
-   `SCC_STATUS_OUTBYUSER`当前用户具有签出文件时设置。  
  
-   `SCC_STATUS_CHECKEDOUT`不能设置，除非`SCC_STATUS_OUTBYUSER`设置。  
  
-   `SCC_STATUS_CHECKEDOUT`仅时该文件已签出到指定的工作目录设置。  
  
-   如果该文件已签出当前用户到工作目录，之外的目录`SCC_STATUS_OUTBYUSER`设置但`SCC_STATUS_CHECKEDOUT`不是。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)
