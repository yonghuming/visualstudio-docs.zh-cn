---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty 方法, IActiveScriptProperty 接口"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
获取由参数指定的属性。  
  
## 语法  
  
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
  
#### 参数  
 `dwProperty`  
 获取属性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 该属性的值。  
  
 `dwProperty` 允许值下表中描述。  
  
|常量|值|含义|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|在整数模式强制脚本引擎部件而不是浮点模式。|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|允许该字符串比较要替换的脚本引擎的功能。|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|通知脚本引擎没有其他脚本引擎存在导致全局对象。|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|强制脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 选择设置要支持的语言功能。  该默认设置 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 支持的语言功能脚本引擎与出现在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的脚本引擎的5.7版设置的语言功能等效。|  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
  
## 备注  
 宿主可以使用SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION属性通知一个脚本引擎没有其他脚本引擎存在导致全局对象。  例如，Internet Explorer会通知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎呈现的页只包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 脚本。  因此，仅 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎可以添加新属性设置为全局对象窗口，因此，不脚本edition \(vbscript\)引擎的Visual Basic执行同样的操作。  引擎忽略此标记或可以使用它来优化添加到全局对象新成员的管理。  
  
 当脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 启动时，宿主可以使用SCRIPTPROP\_INVOKEVERSIONING属性选择设置将支持的语言功能。  如果此特性设置为1 \(SCRIPTLANGUAGEVERSION\_5\_7\)，可用语言语言功能是作为这些出现在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的脚本引擎的5.7版的行为相同。  如果此选项设置为2 \(SCRIPTLANGUAGEVERSION\_5\_8\)，可用语言语言功能会出现在5.7版除了函数外在版本5.8中添加的项。  默认情况下，此属性设置为0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\)，则设置为的语言功能等效出现在5.7版中，除非宿主支持不同的默认行为。  例如，默认情况下，当Internet Explorer 8的文档模式为“Internet Explorer 8个标准”模式时，Internet Explorer 8选择到supporting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语言功能5.8版编写的脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## 请参阅  
 [定义文档兼容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本信息](../../javascript/reference/javascript-version-information.md)