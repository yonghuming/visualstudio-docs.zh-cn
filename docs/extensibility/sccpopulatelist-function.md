---
title: "SccPopulateList 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateList
helpviewer_keywords: SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60f22174ac217a66f860415de898240d41d9a631
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函数
此函数更新的特定源控件命令的文件列表，并提供所有给定文件的源代码管理状态。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 nCommand  
 [in]将应用到中的所有文件的源控件命令`lpFileNames`数组 (请参阅[命令代码](../extensibility/command-code-enumerator.md)有关可用命令的列表)。  
  
 nFiles  
 [in]中的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [in]已知到 IDE 的文件名称的数组。  
  
 pfnPopulate  
 [in]IDE 回调函数调用来添加和删除文件 (请参阅[POPLISTFUNC](../extensibility/poplistfunc.md)有关详细信息)。  
  
 pvCallerData  
 [in]要传递的值未更改对回调函数。  
  
 lpStatus  
 [在中，out]用于源代码管理插件以返回每个文件的状态标志的数组。  
  
 fOptions  
 [in]命令标志 (请参阅的"PopulateList 标志"部分[Bitflags 使用特定命令](../extensibility/bitflags-used-by-specific-commands.md)有关详细信息)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 此函数将检查其当前状态的文件的列表。 它使用`pfnPopulate`回调函数以在文件不匹配的条件时通知调用方`nCommand`。 例如，如果该命令是`SCC_COMMAND_CHECKIN`列表中的文件未签出，然后使用该回调来通知调用方。 有时，源代码管理插件可能会发现无法是命令的一部分并将其添加其他文件。 这样，例如，Visual Basic 用户签出一个.bmp 文件，他或她的项目所使用的但不显示在 Visual Basic 项目文件中。 用户选择**获取**命令在 IDE 中。 IDE 将显示它认为用户可以获取的所有文件的列表，但在该列表显示之前,`SccPopulateList`函数调用以确保要显示的列表是最新。  
  
## <a name="example"></a>示例  
 IDE 来生成它认为用户可以获取的文件的列表。 它将显示此列表之前，它调用`SccPopulateList`函数，这样将有机会到的源代码管理插件添加，并从列表中删除文件。 插件通过调用给定的回调函数修改列表 (请参阅[POPLISTFUNC](../extensibility/poplistfunc.md)有关详细信息)。  
  
 插件继续调用`pfnPopulate`函数，后者添加并删除文件，直到它完成，然后返回从`SccPopulateList`函数。 IDE 然后可以显示其列表。 `lpStatus`数组均表示由 IDE 传入的原始列表中的所有文件。 所有这些文件此外到进行的状态中插件的填充使用回调函数。  
  
> [!NOTE]
>  源代码管理插件始终可以选择只需从此函数，因为它是离开列表立即返回。 如果插件实现此函数，则可以通过设置表示此`SCC_CAP_POPULATELIST`功能首次调用中的位标志[SccInitialize](../extensibility/sccinitialize-function.md)。 默认情况下，插件应始终假设的文件正在传递的所有项。 但是，如果 IDE 设置`SCC_PL_DIR`中标记出来`fOptions`参数，正在传递的所有项都都视为目录。 插件应将添加所属的所有文件的目录中。 IDE 永远不会将传入文件和目录的混合。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Bitflags 由特定的命令](../extensibility/bitflags-used-by-specific-commands.md)   
 [命令代码](../extensibility/command-code-enumerator.md)