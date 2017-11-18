---
title: "IActiveScriptAuthor::AddNamedItem |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
将根级别项的名称添加到引擎的命名空间创作的脚本。 A*根级别项*是可以包含属性和方法，并且，还可以包含事件源的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]查看脚本中的项的名称。 名称必须唯一且可持久化。  
  
 `dwFlags`  
 [in]与命名的项关联的标志。 可以是以下值的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|指示项的名称可用脚本的命名空间中。 这允许访问的项的属性、 方法和事件。<br /><br /> 按照约定，项目的属性包括项的子成员。 因此，所有子对象属性和方法 （和其子成员，以递归方式） 可访问。|  
|SCRIPTITEM_ISSOURCE|0x00000004|指示项的源的事件，该脚本可以脚本事件处理程序。|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|指示项的全局属性和方法与脚本关联的集合。 其成员被编写为全局变量和方法。|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|指示是否已保存创作引擎的脚本应保存该项。|  
|SCRIPTITEM_CODEONLY|0x00000200|表示命名的项表示的仅限代码的对象，它不具有成员来创作。|  
|SCRIPTITEM_NOCODE|0x00000400|表示命名的项就是的名称在添加、，它具有执行任何操作来创作。|  
  
 `pdisp`  
 [in]`IDispatch`的`NamedItem`用于收集方法、 属性或事件源的对象。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)