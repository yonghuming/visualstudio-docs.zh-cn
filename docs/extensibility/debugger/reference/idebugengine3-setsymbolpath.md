---
title: "IDebugEngine3::SetSymbolPath |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetSymbolPath
helpviewer_keywords: IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77a5f294acf60eebc745cb78042e0ea3431fc998
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
设置的路径或调试符号中搜索的路径。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in]包含符号搜索路径的字符串。 有关详细信息，请参阅"备注"。 不能为 null。|  
|`szSymbolCachePath`|[in]包含可以在其中缓存符号的本地路径的字符串。 不能为 null。|  
|`Flags`|[in]不使用;始终设置为 0。|  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 字符串`szSymbolSearchPath`是用分号分隔，搜索符号分隔的一个或多个路径的列表。 这些路径可以是本地路径、 UNC 样式路径或 URL。 这些路径也可以是不同类型的组合。 如果路径是 UNC (例如， \\\Symserver\Symbols)，然后如果路径是到符号服务器，并且应能够从该服务器，它们在缓存中指定的路径加载符号，应确定的调试引擎`szSymbolCachePath`。  
  
 符号路径还可以包含一个或多个缓存位置。 首先，列出按优先级顺序，最高的优先级缓存并隔开缓存 * 符号。 例如:   
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法执行的符号的实际负载。  
  
## <a name="see-also"></a>另请参阅  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)