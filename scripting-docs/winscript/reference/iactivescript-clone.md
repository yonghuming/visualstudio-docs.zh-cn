---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
克隆当前脚本引擎\(减号任何当前执行状态\)，返回没有站点在当前线程上已加载的脚本引擎。  此新脚本引擎属性与原始脚本引擎是属性是相同的，则转换回该初始化状态。  
  
## 语法  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### 参数  
 `ppscript`  
 \[in\]接收指向该克隆的脚本引擎的 [IActiveScript](../../winscript/reference/iactivescript.md) 接口变量的地址。  在处于初始化状态，所以，可用之前，宿主必须创建站点并对新脚本引擎的 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 方法。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|此方法不受支持。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
  
## 备注  
 `IActiveScript::Clone` 方法是 `IPersist*::Save`、 `CoCreateInstance`和 `IPersist*::Load`的优化，因此，新的脚本引擎的状态应是相同的，就象原始脚本引擎的状态已保存和加载到新的脚本引擎。  命名的项目在克隆的脚本引擎副本，但是，每个项目的特定对象指针忘记和获取与 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 方法。  这允许与每个线程的一个相同的对象模型入口点\(\(sta\)模型\)。  
  
 此方法用于运行同一个脚本的多个实例的多线程服务器上使用。  脚本引擎可以返回，`E_NOTIMPL`，在宿主可通过重复该持久状态和创建脚本引擎的新实例实现相同的结果情况下使用 `IPersist*` 接口。  
  
 此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)