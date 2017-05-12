---
title: "IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveNamedItem"
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::RemoveNamedItem
从生成引擎的脚本的命名空间取消 `NamedItem` 对象。  
  
## 语法  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### 参数  
 `pszName`  
 \[in\]标识 `NamedItem` 对象中移除缓冲区的地址。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|`NamedItem` 对象不存在生成引擎的脚本的命名空间。|  
  
## 备注  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 用于插入 `NamedItem` 对象到生成引擎的命名空间的脚本。  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)