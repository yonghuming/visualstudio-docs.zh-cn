---
title: "SccDirDiff 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff 函数"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该函数将显示在客户端磁盘上当前的本地目录和相应的项目受源代码管理之间的差异。  
  
## 语法  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpDirName  
 \[\] in到为其显示可视的差异的本地目录的完全限定的路径。  
  
 dwFlags  
 \[\] in命令标志 \(请参阅备注部分\)。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|在磁盘上的目录是与源代码管理中的项目相同。|  
|SCC\_I\_FILESDIFFER|从源代码管理中的项目的不同磁盘上的目录。|  
|SCC\_I\_RELOADFILE|需要重新加载文件或项目。|  
|SCC\_E\_FILENOTCONTROLLED|目录不是源代码管理下。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定故障。|  
|SCC\_E\_FILENOTEXIST|找不到本地目录。|  
  
## 备注  
 此函数用于指示源代码管理插件以向用户显示的更改到指定的目录列表。 插件，则将其自己的窗口，打开其选择，以显示在磁盘上的用户的目录和相应的项目置于版本控制之下之间的差异的格式。  
  
 如果插件支持的目录的所有比较，它必须按文件名称支持的目录的比较，即使不支持"快速比较"选项。  
  
|`dwFlags`|解释|  
|---------------|--------|  
|SCC\_DIFF\_IGNORECASE|不区分大小写比较 \(可能为快速比较或 visual 使用\)。|  
|SCC\_DIFF\_IGNORESPACE|将忽略空白区域 \(可能为快速比较或 visual 使用\)。|  
|SCC\_DIFF\_QD\_CONTENTS|如果支持源代码管理插件，以无提示方式将该目录，逐字节进行比较。|  
|SCC\_DIFF\_QD\_CHECKSUM|如果插件支持，请以无提示方式比较校验和，通过目录或不受支持，如果回退到 SCC\_DIFF\_QD\_CONTENTS。|  
|SCC\_DIFF\_QD\_TIME|如果支持的插件，请以无提示方式比较其时间戳，通过目录或不受支持，如果回退 SCC\_DIFF\_QD\_CHECKSUM 或 SCC\_DIFF\_QD\_CONTENTS 上。|  
  
> [!NOTE]
>  此函数将使用相同的命令标志作为 [SccDiff](../extensibility/sccdiff-function.md)。 但是，可以选择源代码管理插件不支持目录的"快速比较"操作。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)