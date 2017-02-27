---
title: "SccPopulateList 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList 函数"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可更新特定的源控制命令的文件的列表，并提供所有给定文件的源代码管理状态。  
  
## 语法  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 nCommand  
 \[\] in将应用于所有文件的源代码管理命令 `lpFileNames` 数组 \(请参阅 [命令代码](../extensibility/command-code-enumerator.md) 有关可用命令的列表\)。  
  
 nFiles  
 \[\] in中的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in已知的 IDE 的文件名称的数组。  
  
 pfnPopulate  
 \[\] in要调用来添加和删除文件的 IDE 回调函数 \(请参阅 [POPLISTFUNC](../extensibility/poplistfunc.md) 有关的详细信息\)。  
  
 pvCallerData  
 \[\] in要传递的值未更改的回调函数。  
  
 lpStatus  
 \[in、 out\]用于源代码管理插件以返回每个文件的状态标志的数组。  
  
 选项  
 \[\] in命令标志 \(请参阅的"PopulateList 标志"部分 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md) 有关的详细信息\)。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。|  
  
## 备注  
 此函数将检查其当前状态的文件的列表。 它使用 `pfnPopulate` 回调函数以告知给调用方，当文件不匹配的条件时 `nCommand`。 例如，如果该命令是 `SCC_COMMAND_CHECKIN` 并在列表中的文件未签出，然后使用回调来通知调用方。 有时，源代码管理插件可能会发现的其他文件，可以将命令的一部分并添加它们。 这样，例如，Visual Basic 用户签出一个.bmp 文件，他或她的项目所使用的但不是显示在 Visual Basic 项目文件中。 用户选择 **获取** 命令在 IDE 中。 IDE 将显示它认为用户可以获得的所有文件的列表，但在该列表显示之前, `SccPopulateList` 调用函数，以确保要显示的列表是最新。  
  
## 示例  
 IDE 来生成它认为该用户可以得到的文件的列表。 它显示了此列表之前，它将调用 `SccPopulateList` 函数中，为源代码管理插件提供有机会添加并从列表中删除文件。 插件通过调用给定的回调函数修改的列表 \(请参阅 [POPLISTFUNC](../extensibility/poplistfunc.md) 的更多详细信息\)。  
  
 该插件将继续调用 `pfnPopulate` 函数，它添加和删除文件，直到其完成，然后通过返回 `SccPopulateList` 函数。 IDE 可显示它的列表。`lpStatus` 数组表示通过 IDE 中传递的原始列表中的所有文件。 所有这些文件要让另外的状态插件填写使用回调函数。  
  
> [!NOTE]
>  源代码管理插件始终可以选择只需从该函数，按原样保留列表立即返回。 如果插件实现此函数，它可以指示这一点通过设置 `SCC_CAP_POPULATELIST` 功能在首次调用中的位标志 [SccInitialize](../extensibility/sccinitialize-function.md)。 默认情况下，该插件应始终认为要传入的所有项都是文件。 但是，如果 IDE 设置 `SCC_PL_DIR` 中标记出来 `fOptions` 参数，正在传递的所有项目都都被视为目录。 该插件应将添加所属的所有文件的目录中。 IDE 将永远不会将文件和目录的混合传递。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)   
 [命令代码](../extensibility/command-code-enumerator.md)