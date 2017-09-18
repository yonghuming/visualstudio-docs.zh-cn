---
title: "SccProperties 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties 函数"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccProperties 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该函数将显示文件或项目的源控件属性。  
  
## 语法  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpFileName  
 \[\] in文件或项目的完全限定的路径名称。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|已成功地显示属性。|  
|SCC\_I\_RELOADFILE|版本控制系统已修改文件属性，因此 IDE 应重新加载此文件。|  
|SCC\_E\_PROJNOTOPEN|尚未在源代码管理中打开指定的项目。|  
|SCC\_E\_NOTAUTHORIZED|用户无权查看此文件或项目的属性。|  
|SCC\_E\_FILENOTCONTROLLED|指定的文件或项目不在源代码管理下。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|出现未知或常规错误。|  
  
## 备注  
 源代码管理插件在其自己的对话框中显示的属性。  
  
 这些属性定义由源代码管理插件和插件可能不同于插件。 如果该插件允许用户更改文件的源控件属性，它应返回 `SCC_I_RELOAD` 发出信号 IDE，需要重新加载此文件或项目。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)