---
title: "IActiveScriptProperty::GetProperty |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
获取由参数指定的属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwProperty`  
 要获取的属性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 该属性的值。  
  
 允许值`dwProperty`以下表所述。  
  
|常量|值|含义|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|强制进行分割在整数模式而不是浮动点模式中的脚本引擎。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|允许脚本引擎要替换的字符串比较函数。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|通知没有其他脚本引擎存在于全局对象提供的脚本引擎。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|强制[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本引擎选择的语言功能来支持一组。 默认的支持的语言功能集[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本引擎相当于 5.7 版本中出现的语言功能集[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本引擎。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
  
## <a name="remarks"></a>备注  
 主机可以使用 SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION 属性以通知没有其他脚本引擎存在于全局对象提供的脚本引擎。 例如，Internet 资源管理器可以告诉[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]呈现的页面仅包含的引擎[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本。 因此，仅[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎可以将新属性添加到全局对象窗口中，并且没有任何 Visual Basic Scripting Edition (VBScript) 引擎执行相同的。 该引擎可以忽略此标志，或可以使用它来优化添加到全局对象的新成员的管理。  
  
 主机可以使用 SCRIPTPROP_INVOKEVERSIONING 属性选择的语言功能是一组支持时[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本引擎已启动。 如果此属性设置为 1 (SCRIPTLANGUAGEVERSION_5_7)，可用的语言功能是相同的与版本 5.7 中出现[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]脚本引擎。 如果它设置为 2 (SCRIPTLANGUAGEVERSION_5_8)，可用的语言功能所出现版本 5.7 除了版本 5.8 中添加了的功能中。 默认情况下，此属性设置为 0 (SCRIPTLANGUAGEVERSION_DEFAULT)，除非主机支持不同的默认行为，这是等效于在版本 5.7 中, 出现的语言功能集。 例如，Internet Explorer 8 opts 到[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]版本 5.8 支持的语言功能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]默认情况下，对 Internet Explorer 8 文档模式为"Internet Explorer 8 标准"模式时的脚本引擎。  
  
## <a name="see-also"></a>另请参阅  
 [定义文档兼容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本信息](../../javascript/reference/javascript-version-information.md)