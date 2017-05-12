---
title: "JS_PROPERTY_MEMBERS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_MEMBERS
apilocation: jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JS_PROPERTY_MEMBERS 枚举
在对象成员的请求中用于指定信息类型返回的标志。  
  
## 语法  
  
```  
enum JS_PROPERTY_MEMBERS  
{  
   JS_PROPERTY_MEMBERS_ALL = 0,  
   JS_PROPERTY_MEMBERS_ARGUMENTS = 1  
} JS_PROPERTY_MEMBERS;  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`JS_PROPERTY_MEMBERS_ALL`|表示请求枚举所有成员。|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|表示请求枚举仅参数。|  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)