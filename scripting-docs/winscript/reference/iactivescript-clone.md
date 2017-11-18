---
title: "IActiveScript::Clone |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
克隆当前脚本引擎 （减去任何当前执行状态），返回当前线程中没有站点加载脚本引擎。 此新的脚本引擎的属性将与原始脚本引擎将会处于如果它已转换回初始化状态的属性完全相同。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppscript`  
 [out]接收指向的变量的地址[IActiveScript](../../winscript/reference/iactivescript.md)克隆的脚本引擎的接口。 主机必须创建一个站点，并调用[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)上新的脚本引擎之后，它才会处于初始化状态的方法，因此，可用。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|不支持此方法。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
  
## <a name="remarks"></a>备注  
 `IActiveScript::Clone`方法是一种优化的`IPersist*::Save`， `CoCreateInstance`，和`IPersist*::Load`，因此就像原始脚本引擎的状态已保存和加载到新的脚本引擎的新的脚本引擎的状态应相同。 已命名的项会有重复中克隆的脚本引擎，但每个项的特定对象指针会忘记和所获得的采用[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)方法。 这允许与每个线程入口点 （单元模型） 使用的相同对象模型。  
  
 此方法适用于可以运行同一个脚本的多个实例的多线程的服务器主机。 脚本引擎可能会返回`E_NOTIMPL`，在这种情况下，主机可以复制的持久状态，并创建中的脚本引擎的新实例来实现相同的结果`IPersist*`接口。  
  
 此方法可以从非基本线程调用不会导致为主机对象或设置为非基本标注[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)