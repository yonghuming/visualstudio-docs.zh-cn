---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem 方法, IActiveScript 接口"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
添加一个根级项目的名称改为脚本引擎的命名空间。  一个根级项目与属性的对象和方法，事件源，或所有这三个。  
  
## 语法  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### 参数  
 `pstrName`  
 \[in\]包含项目的名称范围从脚本缓冲区的地址。  该名称必须唯一和持久。  
  
 `dwFlags`  
 \[in\]标志与项目。  可以是这些值的组合：  
  
|值|含义|  
|-------|--------|  
|SCRIPTITEM\_CODEONLY|指示命名项表示编码对象，并且，宿主没有 `IUnknown` 将与此代码对象。  宿主只有一个名称此对象。  在面向对象的语言\(例如C\+\+，此标记将创建选件类。  并非所有的语言支持此标志。|  
|SCRIPTITEM\_GLOBALMEMBERS|指示该项目是全局属性和方法的集合与该脚本。  通常，一个脚本引擎将忽略对象名\(除了为使用它的用途外作为cookie [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 方法的，或者解决的显式范围\)并显示其成员作为全局变量和方法。  这使宿主能够为该脚本扩展可用的库\(运行时函数等\)。  它会将向脚本引擎处理名称冲突\(例如，那么，当两个SCRIPTITEM\_GLOBALMEMBERS项目具有相同名称的方法\)时，因此，虽然错误不应是返回的情况。|  
|SCRIPTITEM\_ISPERSISTENT|指示应保存项目，如果脚本引擎保存。  同样，设置该标志指示回该初始化状态的转换应保留项目的名称和类型信息，但是，\(脚本引擎必须释放所有指针对实际对象的接口\)。|  
|SCRIPTITEM\_ISSOURCE|指示该脚本可以接收的项目源事件。  子对象\(表示在这些对象\)对象的属性还能发出事件设置为脚本。  这不是递归的，但是，这种常见的，例如，创建容器和所有提供了一种便捷机制其成员控件。|  
|SCRIPTITEM\_ISVISIBLE|指示项目的名称可在脚本的命名空间，允许对特性的访问，该项目的方法和事件。  按照约定该项目的属性包括项的子项;因此，所有子级对象的属性和方法\(及其子级，递归\)进行访问。|  
|SCRIPTITEM\_NOCODE|指示该项目是添加到脚本的命名空间的名称，不应处理代码应关联的项目。  例如，在中，不使用此设置标志，VBScript将创建一个名为项目的单独模块，因此，C\+\+可能创建命名项目的单独包装选件类。|  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)