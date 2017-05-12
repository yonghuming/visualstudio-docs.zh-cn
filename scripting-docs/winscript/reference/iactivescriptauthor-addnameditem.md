---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
添加一个根级项目的名称改为生成引擎的命名空间的脚本。  一个 *根级项目* 是可以包含属性和方法，即，也可以包含事件源的对象。  
  
## 语法  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### 参数  
 `pszName`  
 \[in\]项目的名称范围从脚本。  该名称必须唯一和持久。  
  
 `dwFlags`  
 \[in\]与命名项目的标志。  可为下列值的组合：  
  
|常量|值|说明|  
|--------|-------|--------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|指示项目的名称可在脚本的命名空间。  这允许到项目的属性、方法和事件的访问。<br /><br /> 按照约定，该项目的属性包括项的子成员。  因此，所有子级对象的属性和方法\(及其子成员，递归\)进行访问。|  
|SCRIPTITEM\_ISSOURCE|0x00000004|指示项目源的事件该脚本可以有脚本事件处理程序。|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|指示该项目是与该脚本全局属性的集合和方法。  其成员生成作为全局变量和方法。|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|指示应保存项目，如果生成引擎的脚本保存。|  
|SCRIPTITEM\_CODEONLY|0x00000200|指示命名项表示编码对象和它没有生成的成员。|  
|SCRIPTITEM\_NOCODE|0x00000400|不指示命名项目是添加到的名称并具有创作。|  
  
 `pdisp`  
 \[in\]用于收集方法、属性或事件源 `NamedItem` 对象的 `IDispatch`。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)