---
title: "SccWillCreateSccFile 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile 函数"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccWillCreateSccFile 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将确定源代码管理插件是否支持 MSSCCPRJ 的创建。每个给定的文件的源代码管理文件。  
  
## 语法  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 nFiles  
 \[\] in文件名称中包含数目 `lpFileNames` 数组的长度以及 `pbSccFiles` 数组。  
  
 lpFileNames  
 \[\] in若要检查的完全限定的文件名称的数组 \(数组必须由调用方已分配\)。  
  
 pbSccFiles  
 \[in、 out\]要在其中存储结果的数组。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_INVALIDFILEPATH|一个数组中的路径无效。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。|  
  
## 备注  
 此函数调用的文件，以确定是否 MSSCCPRJ 中支持的源代码管理插件的列表。源代码管理文件为每个给定文件 \(用于 MSSCCPRJ 的详细信息。源代码管理文件，请参阅 [MSSCCPRJ。源代码管理文件](../extensibility/mssccprj-scc-file.md)\)。 源代码管理插件可以声明它们是否具有创建 MSSCCPRJ 的功能。通过声明的 SCC 文件 `SCC_CAP_SCCFILE` 在初始化过程中。 该插件返回 `TRUE` 或 `FALSE` 每个文件中 `pbSccFiles` 数组指示的给定文件具有 MSSCCPRJ。SCC 的支持。 如果该插件从函数返回成功代码，将遵循返回数组中的值。 在失败时，该数组将被忽略。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ。源代码管理文件](../extensibility/mssccprj-scc-file.md)