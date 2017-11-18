---
title: "IActiveScript::GetScriptDispatch |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
检索`IDispatch`接口的方法和属性与当前正在运行的脚本相关联。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrItemName`  
 [in]包含调用方需要关联的调度对象的项的名称的缓冲区地址。 如果此参数为`NULL`，调度对象包含作为其成员的所有全局方法和属性定义的脚本。 通过`IDispatch`接口和关联`ITypeInfo`接口，宿主可以调用脚本方法或视图并修改脚本变量。  
  
 `ppdisp`  
 [out]接收一个指针，到与脚本的全局方法和属性关联的对象的变量的地址。 如果脚本引擎不支持此类对象，`NULL`返回。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
|`S_FALSE`|脚本引擎不支持调度的对象;`ppdisp`参数设置为 NULL。|  
  
## <a name="remarks"></a>备注  
 因为可以通过调用添加方法和属性[IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)接口，`IDispatch`新方法和属性，可以动态支持此方法返回的接口。 同样，`IDispatch::GetTypeInfo`方法应返回一个新的唯一`ITypeInfo`接口添加方法和属性时。 但请注意，语言引擎不得更改`IDispatch`中方式是否与不兼容任何接口以前`ITypeInfo`返回的接口。 例如，这意味着 Dispid 都将永远不会重复使用。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)