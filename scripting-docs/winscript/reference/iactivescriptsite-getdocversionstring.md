---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
检索唯一标识当前文件版本的宿主中定义的字符串。  如果相关文档更改了Windows脚本的范围之外\(如在编辑器与记事本\)的HTML页，脚本引擎可与其保持的状态一起保存此，强制重新编译，则下次该脚本加载。  
  
## 语法  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### 参数  
 `pstrVersionString`  
 \[in\]宿主中定义的地址文档版本字符串。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_NOTIMPL`，则此方法不受支持。  
  
## 备注  
 如果 `E_NOTIMPL` 返回，脚本引擎应该假定，该脚本与同步文档。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)