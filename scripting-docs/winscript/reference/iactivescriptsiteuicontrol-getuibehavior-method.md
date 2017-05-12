---
title: "IActiveScriptSiteUIControl::GetUIBehavior 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior 方法
获取表示方法应处理UI控件的 [SCRIPTUICHANDLING 枚举](../../winscript/reference/scriptuichandling-enumeration.md)。  
  
## 语法  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### 参数  
 `UicItem`  
 控件的类型。  
  
 `pUicHandling`  
 应已处理种控件。