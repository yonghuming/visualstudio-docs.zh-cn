---
title: "SccDiff 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDiff"
helpviewer_keywords: 
  - "SccDiff 函数"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccDiff 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数显示 \(或 \(可选\) 只需检查\) 控制系统的源中当前文件 \(在本地硬盘上\) 和其最后一个签入版本之间的差异。  
  
## 语法  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpFileName  
 \[\] in为其请求差异文件的名称。  
  
 选项  
 \[\] in命令的标志。 有关详细信息，请参阅备注。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|工作副本和服务器版本是相同的。|  
|SCC\_I\_FILESDIFFERS|在源代码管理下的版本不同的工作副本。|  
|SCC\_I\_RELOADFILE|需要重新加载文件或项目。|  
|SCC\_E\_FILENOTCONTROLLED|文件不是源代码管理下。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NONSPECIFICERROR|模糊失败;无法获得文件差异。|  
|SCC\_E\_FILENOTEXIST|找不到本地文件。|  
  
## 备注  
 此函数有两个不同的用途。 默认情况下，它显示的更改的列表文件。 源代码管理插件将自己的窗口，打开任意格式选择，则若要显示在磁盘上的用户的文件和源代码管理下的文件的最新版本之间的差异。  
  
 或者，IDE 可能只需确定文件是否已更改。 例如，IDE 可能需要确定它是否可以安全地签出文件，而不通知用户。 在这种情况下，IDE 会将传递在 `SCC_DIFF_CONTENTS` 标志。 源代码管理插件必须检查在磁盘上，按字节，针对受源代码管理文件的文件，并返回一个值，该值指示两个文件是否不同不向用户显示任何内容。  
  
 作为一种性能优化，源代码管理插件可能会使用基于校验和或时间戳而不是逐字节比较的所要求的替代方法 `SCC_DIFF_CONTENTS`: 这些窗体的比较是很明显越快，但可靠性较低。 并非所有的源代码管理系统可能会支持这些替换比较方法，并且该插件可能需要回退到内容比较。 所有源控制插件最低限度上，必须都支持的内容比较。  
  
> [!NOTE]
>  快速差异标志是互斥的。 有效传递任何标志，但不是有效的同时将多个传递。`SCC_DIFF_QUICK_DIFF`, 它一个屏蔽，它将合并所有标志，可用于测试，但绝对不应作为参数传递。  
  
|`fOption`|含义|  
|---------------|--------|  
|SCC\_DIFF\_IGNORECASE|不区分大小写比较 \(可能为快速或可视化差异使用\)。|  
|SCC\_DIFF\_IGNORESPACE|将忽略空白区域 \(可能为快速或可视化差异使用\)。|  
|SCC\_DIFF\_QD\_CONTENTS|以无提示方式将该文件，逐字节进行比较。|  
|SCC\_DIFF\_QD\_CHECKSUM|以无提示方式将通过校验和时支持的文件进行比较。 如果不支持，将回退到内容的比较。|  
|SCC\_DIFF\_QD\_TIME|以无提示方式将通过其时间戳时支持的文件进行比较。 如果不支持，将回退到内容的比较。|  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)