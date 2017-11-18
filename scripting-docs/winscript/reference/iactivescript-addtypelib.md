---
title: "IActiveScript::AddTypeLib |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
将类型库添加到脚本的命名空间。 它类似于`#include`C/c + + 中的指令。 它允许一组预定义的类定义，如项`typedefs`，并命名要添加到运行时环境提供给脚本使用的常量。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>参数  
 `guidTypeLib`  
 [in]若要添加的类型库的 CLSID。  
  
 `dwMaj`  
 [in]主版本号。  
  
 `dwMin`  
 [in]次版本号。  
  
 `dwFlags`  
 [in]选项的标志。 可以是以下值：  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|类型库描述主机所使用的 ActiveX 控件。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
|`TYPE_E_CANTLOADLIBRARY`|无法加载指定的类型库。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)