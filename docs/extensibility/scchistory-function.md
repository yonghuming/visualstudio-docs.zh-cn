---
title: "SccHistory 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory 函数"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccHistory 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将显示指定的文件的历史记录。  
  
## 语法  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 `pvContext`  
 \[\] in源控制插件上下文结构。  
  
 `hWnd`  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 `nFiles`  
 \[\] in中指定的文件数 `lpFileName` 数组。  
  
 `lpFileName`  
 \[\] in文件的完全限定名称的数组。  
  
 `fOptions`  
 \[\] in\(当前未使用\) 的命令标志。  
  
 `pvOptions`  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功获取版本历史记录。|  
|SCC\_I\_RELOADFILE|源代码管理系统实际上在情况下修改磁盘上的文件提取历史记录 \(例如，通过获取的旧版本\)，因此 IDE 应重新加载此文件。|  
|SCC\_E\_FILENOTCONTROLLED|文件不是源代码管理下。|  
|SCC\_E\_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_PROJNOTOPEN|该项目是已打开。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。 无法获得文件历史记录。|  
  
## 备注  
 源代码管理插件可以显示其自己的对话框来显示每个文件的历史记录使用 `hWnd` 作为父窗口。 或者，可选的文本输出回调函数提供给 [SccOpenProject](../extensibility/sccopenproject-function.md) 可用，如果它受支持。  
  
 请注意，在某些情况下，此调用的执行期间可能会更改所检查的文件。 例如， [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] history 命令使用户有机会以获取文件的旧版本。 在这种情况下，源代码管理插件返回 `SCC_I_RELOAD` 警告 IDE，需要重新加载该文件。  
  
> [!NOTE]
>  如果源代码管理插件不支持此函数对于一组文件，可以显示仅的文件历史记录的第一个文件。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)