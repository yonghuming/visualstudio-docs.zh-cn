---
title: "SccAddFilesFromSCC 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC 函数"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFilesFromSCC 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数会从源代码管理文件的列表添加到当前打开的项目。  
  
## 语法  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文指针。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpUser  
 \[in、 out\]\(最多 SCC\_USER\_SIZE，包括 null 结束符\) 用户名。  
  
 lpAuxProjPath  
 \[in、 out\]标识项目的辅助字符串 \(最多 `SCC_PRJPATH_`的大小，包括 null 结束符\)。  
  
 cFiles  
 \[\] in由给定的文件数 `lpFilePaths`。  
  
 lpFilePaths  
 \[in、 out\]要添加到当前项目的文件名的数组。  
  
 lpDestination  
 \[\] in从中对文件进行写入目标路径。  
  
 lpComment  
 \[\] in要应用于每个要添加的文件的注释。  
  
 pbResults  
 \[in、 out\]设置为指示已成功 \(非零或 TRUE\) 或失败的标志的数组 \(0 或 FALSE\) 为每个文件 \(数组的大小必须至少为 `cFiles` 长\)。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_E\_PROJNOTOPEN|项目未打开。|  
|SCC\_E\_OPNOTPERFORMED|连接不是连接到与指定的相同的项目 `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|未授权用户来更新数据库。|  
|SCC\_E\_NONSPECIFICERROR|出现未知的错误。|  
|SCC\_I\_RELOADFILE|需要重新加载文件或项目。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)