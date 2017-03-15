---
title: "SccEnumChangedFiles 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "SccEnumChangedFiles 函数"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccEnumChangedFiles 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有了本地文件的列表，此函数可确定哪些文件是与源代码控制数据库中的对应版本不同。  
  
## 语法  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 cFiles  
 \[\] in中指定的文件名称数目 `lpFileNames` 数组。 此外指定了大小 `plIsFileDifferent` 数组。  
  
 lpFileNames  
 \[\] in若要检查的本地文件名称的数组。  
  
 plIsFileDifferent  
 \[in、 out\]值，该值指示每个文件的差异状态数组 \(数组必须至少具有 `cFiles` 条目\)。 该文件是不同的非零值表示。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|操作已成功完成。|  
|SCC\_UNSPECIFIEDERROR|一般错误。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)