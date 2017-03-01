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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a178aada6303ed21f51a6be66ba02b2145dcd694
ms.lasthandoff: 02/22/2017

---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函数
此函数可获取一组在源代码管理下的所选文件的状态信息。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控制插件上下文结构。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组和长度`lpStatus`数组。  
  
 lpFileNames  
 [in]要查询的文件的名称的数组。  
  
 lpStatus  
 [in、 out]数组中的源代码管理插件返回的每个文件的状态标志。 有关详细信息，请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回下列值之一︰  
  
|值|说明|  
|-----------|-----------------|  
|SCC_OK|查询已成功。|  
|SCC_E_ACCESSFAILURE|没有与访问源代码管理系统，可能引起的网络和资源争用问题的问题。 建议重试。|  
|SCC_E_PROJNOTOPEN|未受源代码管理打开项目。|  
|SCC_E_NONSPECIFICERROR|非特定故障。|  
  
## <a name="remarks"></a>备注  
 如果`lpFileName`为空字符串，当前没有要更新的状态信息。 否则，很可能已更改的状态信息的文件的完整路径名称。  
  
 返回的数组可以是一个位屏蔽的`SCC_STATUS_xxxx`bits。 有关详细信息，请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)。 源代码管理系统可能不支持所有的位类型。 例如，如果`SCC_STATUS_OUTOFDATE`未提供，不只是设置了位。  
  
 使用此函数时签出文件，请注意以下`MSSCCI`状态要求︰  
  
-   `SCC_STATUS_OUTBYUSER`在当前用户已签出文件时设置。  
  
-   `SCC_STATUS_CHECKEDOUT`不能设置，除非`SCC_STATUS_OUTBYUSER`设置。  
  
-   `SCC_STATUS_CHECKEDOUT`时，才设置该文件已签出到指定的工作目录。  
  
-   如果该文件已签出由当前用户之外的工作目录的目录到`SCC_STATUS_OUTBYUSER`设置但`SCC_STATUS_CHECKEDOUT`不是。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)
