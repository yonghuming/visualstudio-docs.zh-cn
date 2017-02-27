---
title: "SccGetUserOption 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption 函数"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetUserOption 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可检索各种特定于用户的选项。  
  
## 语法  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 nOption  
 \[\] in要检索 \(有关可能的选项，请参阅备注\) 的选项。  
  
 lpVal  
 \[\] out与选项相关联的值。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|已成功检索选项。|  
|SCC\_E\_OPNOTSUPPORTED|不支持选项。|  
|SCC\_E\_NONSPECIFICERROR|出现未知的错误。|  
  
## 备注  
 此命令支持以下选项:  
  
|用户选项|说明|  
|----------|--------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|确定用户是否希望签出文件的本地版本。`lpVal` 分配 `SCC_USEROPT_COLV_YES` \(用户想要签出本地文件\) 或 `SCC_USEROPT_COLV_NO`。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [错误代码](../extensibility/error-codes.md)