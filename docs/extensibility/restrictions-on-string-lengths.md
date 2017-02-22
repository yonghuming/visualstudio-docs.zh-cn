---
title: "字符串长度限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，字符串长度限制"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 字符串长度限制
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

源控制插件 API 限制在各种函数中使用的字符串的长度。  
  
## 字符串长度值  
  
|返回的常量|值|  
|-----------|-------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  长度不包括终止 `null`。 其他常量与而不是"\_LEN"的"\_SIZE"后缀不包括空间用于终止 `null`。  
  
|返回的常量|值|  
|-----------|-------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)