---
title: "IDispError::GetSource |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 922f95206d341773632b84c3922ea3b240d8d1ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
返回的类或引发错误的应用程序依赖于语言的编程标识符。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrSource`  
 [out]包含窗体中的编程标识符的字符串`progname.objectname`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法用于确定类或应用程序何处出现异常。 指定由在调用时提供的区域设置标识符 (LCID) 的语言，可能返回的编程标识符。  
  
> [!NOTE]
>  未实现此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)