---
title: "SCRIPTPROP_HOSTKEEPALIVE 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE 属性
用于指定是否应保持脚本引擎完整功能，如果具有未处理的引用。  
  
 使用 [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) 将此属性设置为 `true`。  如果此特性设置为 `true`，脚本引擎时保持完整功能，只要至少有一个处理引用或嵌入脚本引擎或向 JavaScript 对象的一 `IDispatch` 指针使用创建脚本引擎。  当此属性设置为 `true`时，使用 [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) 或 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 方法，您不应显式关闭或重新设置脚本引擎。  的最后释放对脚本对象关闭脚本引擎。  
  
## 语法  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## 要求  
 此属性仅显示在安装与 [!INCLUDE[win8](../../javascript/includes/win8-md.md)]，使用 Internet Explorer 8 的 2707082 KB 在 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或者使用 Internet Explorer 9 的 2722913 KB 在 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] 或 [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]activscp.idl 的版本。