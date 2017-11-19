---
title: "IActiveScriptAuthor::AddTypeLib |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 150628f1822c721f1e349005de457951e226ef1b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
将类型库添加到脚本的命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>参数  
 `rguidTypeLib`  
 [in]CLSID （类标识符） 的类型库添加。  
  
 `dwMajor`  
 [in]主版本号。  
  
 `dwMinor`  
 [in]次版本号。  
  
 `dwFlags`  
 [in]未使用。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法调用`LoadTypeLib`可加载类型库。 此方法调用成功之后，`IActiveScriptAuthor::AddNamedItem`添加类型信息。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/en-us/155b48e5-5438-409e-9342-630a6a500f60)