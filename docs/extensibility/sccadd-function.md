---
title: "SccAdd 函数 | Microsoft Docs"
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
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd 函数"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAdd 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将新文件添加到源代码管理系统。  
  
## 语法  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 nFiles  
 \[\] in选择要添加到当前项目中给定的相同的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in要添加的文件的完全限定本地名称的数组。  
  
 lpComment  
 \[\] in要应用于所有要添加的文件的注释。  
  
 pfOptions  
 \[\] in在每个文件基础上提供的命令标志的数组。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|添加操作已成功。|  
|SCC\_E\_FILEALREADYEXISTS|所选的文件已位于源代码管理下。|  
|SCC\_E\_TYPENOTSUPPORTED|源代码管理系统不支持的文件 \(例如二进制\) 的类型。|  
|SCC\_E\_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_NONSPECIFICERROR|模糊失败;添加不会执行。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消了操作。|  
|SCC\_I\_RELOADFILE|需要重新加载文件或项目。|  
|SCC\_E\_FILENOTEXIST|找不到本地文件。|  
  
## 备注  
 常用 `fOptions` 此处替换为一个数组， `pfOptions`, ，其中一个 `LONG` 选项规范，每个文件。 这是因为文件类型而有所不同多个文件。  
  
> [!NOTE]
>  无效两者都指定 `SCC_FILETYPE_TEXT` 和 `SCC_FILETYPE_BINARY` 选项相同的文件，但它是有效既不指定。 设置既不是设置相同 `SCC_FILETYPE_AUTO`, ，在这种情况下，源代码管理插件自动检测的文件类型。  
  
 下面是在使用的标志列表 `pfOptions` 数组:  
  
|选项|值|含义|  
|--------|-------|--------|  
|SCC\_FILETYPE\_AUTO|0x00|源代码管理插件应该会检测到的文件类型。|  
|SCC\_FILETYPE\_TEXT|0x01|指示一个 ASCII 文本文件。|  
|SCC\_FILETYPE\_BINARY|0x02|指示文件类型而非 ASCII 文本。|  
|SCC\_ADD\_STORELATEST|0x04，则|存储仅该文件，没有增量的最新副本。|  
|SCC\_FILETYPE\_TEXT\_ANSI|0x08|将该文件视为 ANSI 文本。|  
|SCC\_FILETYPE\_UTF8|0x10|将该文件视为 UTF8 格式中的 Unicode 文本。|  
|SCC\_FILETYPE\_UTF16LE|0x20|将该文件视为 Unicode 文本中 UTF16 Little Endian 格式。|  
|SCC\_FILETYPE\_UTF16BE|0x40|将文件另存为 UTF16 Big Endian Unicode 文本设置格式。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)