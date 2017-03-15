---
title: "SccQueryChanges 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges 函数"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccQueryChanges 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数枚举给定的文件的列表，对于通过回调函数的每个文件提供名称更改的信息。  
  
## 语法  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 nFiles  
 \[\] in中的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in要获取其相关信息的文件名的数组。  
  
 pfnCallback  
 \[\] in输入列表中每个文件的名称调用的回调函数 \(请参阅 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 有关的详细信息\)。  
  
 pvCallerData  
 \[\] in将被原样传递给回调函数的值。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|查询处理已成功完成。|  
|SCC\_E\_PROJNOTOPEN|尚未在源代码管理中打开该项目。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。|  
|SCC\_E\_NONSPECIFICERROR|未指定或为常规时出错。|  
  
## 备注  
 要查询的更改是对该命名空间: 具体而言，重命名、 添加和删除文件。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [错误代码](../extensibility/error-codes.md)