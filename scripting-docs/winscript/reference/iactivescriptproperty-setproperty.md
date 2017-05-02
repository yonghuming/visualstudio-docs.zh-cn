---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty 方法, IActiveScriptProperty 接口"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
设置由参数指定的属性。  
  
## 语法  
  
```  
HRESULT SetProperty(  
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
 要设置的属性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 该属性的值。  
  
 `dwProperty` 允许值下表中描述。  
  
|常量|值|含义|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|在整数模式强制脚本引擎部件而不是浮点模式。  默认值为 `False`。|  
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
 若要启用或禁用整除，请调用 `SetProperty` 并将 `Boolean` 为 `Object`。  默认情况下，属性值为 `False`。  如果将其设置为 `True`，除法运算将只返回整数。  
  
 若要启用或禁用自定义字符串比较，请调用 `SetProperty` 然后按 `Object` 值。  您传递的对象必须实现接口 [IActiveScriptStringCompare 接口](../../winscript/reference/iactivescriptstringcompare-interface.md)。  [IActiveScriptStringCompare 接口](../../winscript/reference/iactivescriptstringcompare-interface.md) 接口的 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) 方法都会调用字符串比较函数执行。  
  
 若要选择设置要支持的语言功能，当脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 初始化时，请调用 `SetProperty` 并将对应于设置的语言功能。SCRIPTPROP\_INVOKEVERSIONING启用的值。  如果此特性设置为1 \(SCRIPTLANGUAGEVERSION\_5\_7\)，可用语言语言功能是作为这些出现在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的脚本引擎的5.7版的行为相同。  如果此选项设置为2 \(SCRIPTLANGUAGEVERSION\_5\_8\)，可用语言语言功能会出现在版本5.7除新功能外在版本5.8中添加的项。  默认情况下，此属性设置为0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\)，则设置为的语言功能等效出现在5.7版中，除非宿主支持不同的默认行为。  例如，Internet Explorer 8选择到默认情况下由5.8版编写的脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 支持的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语言功能，则默认文档Internet Explorer 8的模式为“Internet Explorer 8种标准”模式时。  切换Internet Explorer 8文档模式为Internet Explorer 7个标准或突发模式重置脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 支持存在于5.7版的脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 设置的语言功能。  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING，仅当脚本引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 初始化时，应设置。  
  
## 示例  
 下面的示例演示如何强制脚本引擎使用整除以及如何允许重载相比功能。  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## 请参阅  
 [定义文档兼容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本信息](../../javascript/reference/javascript-version-information.md)