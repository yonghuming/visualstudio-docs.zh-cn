---
title: "IActiveScript::AddNamedItem |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
将根级别项的名称添加到脚本引擎的命名空间。 根级别项是具有属性和方法、 事件源或所有三个的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrName`  
 [in]查看脚本中包含的项名称的缓冲区地址。 名称必须唯一且可持久化。  
  
 `dwFlags`  
 [in]与项目关联的标志。 可以是这些值的组合：  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|指示命名的项表示仅限代码的对象，并且该主机没有`IUnknown`要与此仅限代码的对象相关联。 主机仅具有此对象的名称。 在 c + + 等面向对象语言中，此标志将创建一个类。 并非所有语言都支持此标志。|  
|SCRIPTITEM_GLOBALMEMBERS|指示项全局属性和方法与脚本相关联的集合。 通常情况下，脚本引擎将忽略的对象名称 (以外为了将其作为 cookie [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法，或用于解决显式作用域) 和公开其成员为全局变量和方法。 这允许宿主扩展库 （运行时函数和等等） 对该脚本可用。 它从左到脚本引擎以处理名称冲突 （例如，当两个 SCRIPTITEM_GLOBALMEMBERS 项具有相同名称的方法），但由于这种情况下应不会返回错误。|  
|SCRIPTITEM_ISPERSISTENT|指示是否保存脚本引擎应保存该项。 同样，设置此标志指示回初始化状态的转换应保留 （脚本引擎必须但是，释放所有指向实际对象上的接口） 的项的名称和类型信息。|  
|SCRIPTITEM_ISSOURCE|指示项源脚本可以接收的事件。 子对象 （该对象的属性，是对象本身） 还可以发出事件的脚本。 这不是递归的但它提供的方便机制最常见的情况下，例如，创建一个容器和其成员的所有控件。|  
|SCRIPTITEM_ISVISIBLE|指示项的名称是在该脚本中，允许访问属性、 方法和事件的项的命名空间中可用。 按照约定的项的属性包括项的子级;因此，所有子对象属性和方法 （以及其子项，以递归方式） 将可访问。|  
|SCRIPTITEM_NOCODE|指示，项是只是要添加到脚本的命名空间的名称，并且不应视为代码应为其关联的项。 例如，如果没有设置此标志，VBScript 将创建命名项，单独的模块和 c + + 可能会创建一个单独的包装类，命名的项。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)