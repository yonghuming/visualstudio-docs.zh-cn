---
title: "IDebugDocumentInfo::GetDocumentClassId |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be3d29cf19752da18b76f31b4d12cecb05592c00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
返回`CLSID`标识文档类型。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pclsidDocument`  
 [out]A`CLSID`标识文档类型。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法允许对此文档的主机自定义查看器的调试器 IDE。  
  
 如果文档没有可查看的数据的返回值`pclsidDocument`是`CLSID_NULL`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentInfo 接口](../../winscript/reference/idebugdocumentinfo-interface.md)