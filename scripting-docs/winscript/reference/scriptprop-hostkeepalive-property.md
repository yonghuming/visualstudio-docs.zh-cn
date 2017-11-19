---
title: "SCRIPTPROP_HOSTKEEPALIVE 属性 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE 属性
用于指定应保持脚本引擎完全正常运行，如果有未处理引用。  
  
 使用[IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md)若要将此属性设置为`true`。 如果此属性设置为`true`，脚本引擎保持完全正常运行，只要没有至少一个未完成的引用到脚本引擎本身或`IDispatch`指向由使用的脚本创建的 JavaScript 对象引擎。 当此属性设置为`true`，你应未显式关闭，或通过使用重置脚本引擎[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)或[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)方法。 对脚本对象的最后引用的版本将关闭脚本引擎。  
  
## <a name="syntax"></a>语法  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>要求  
 此属性只 activscp.idl 一起安装的版本中将出现[!INCLUDE[win8](../../javascript/includes/win8-md.md)]，与用于在 Internet Explorer 8 KB 2707082 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或与 Internet 资源管理器上的 9 KB 2722913[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]或[!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]。