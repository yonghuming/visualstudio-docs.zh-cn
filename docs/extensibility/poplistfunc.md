---
title: "POPLISTFUNC | Microsoft Docs"
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
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "POPLISTFUNC 回调函数"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此回调提供给 [SccPopulateList](../extensibility/sccpopulatelist-function.md) ide 和源代码管理插件用于更新的文件或目录的列表 \(还提供给 `SccPopulateList` 函数\)。  
  
 当用户选择 **获取** 命令在 IDE 中，则 IDE 将显示用户可以获得的所有文件的列表框。 遗憾的是，IDE 不知道该用户可能会得到; 的所有文件的确切列表只有插件都有此列表。 如果其他用户将文件添加到源代码管理项目，这些文件应出现在列表中，但 IDE 并不了解它们。 IDE 来生成它认为用户可以获得文件的列表。 它向用户显示此列表之前，它将调用 [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` 为源代码管理插件提供一个机会来添加并从列表中删除文件。  
  
## 签名  
 源代码管理插件修改通过调用以下原型使用 IDE 实现的函数的列表:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## 参数  
 pvCallerData  
 `pvCallerData` 参数由呼叫方 \(IDE\) 传递给 [SccPopulateList](../extensibility/sccpopulatelist-function.md)。 源代码管理插件应假定此参数的内容执行任何操作。  
  
 fAddRemove  
 如果 `TRUE`, ，`lpFileName` 是应添加到文件列表的文件。 如果 `FALSE`, ，`lpFileName` 是应从文件列表中删除一个文件。  
  
 nStatus  
 状态 `lpFileName` \(的组合 `SCC_STATUS` 位; 请参阅 [文件状态代码](../extensibility/file-status-code-enumerator.md) 有关的详细信息\)。  
  
 lpFileName  
 要添加或从列表中删除的文件名称的完整目录路径。  
  
## 返回值  
  
|值|描述|  
|-------|--------|  
|`TRUE`|该插件可以继续调用此函数。|  
|`FALSE`|在 IDE 端 \(如内存的情况下扩展\) 已有问题。 该插件应停止操作。|  
  
## 备注  
 对于每个源代码管理插件想要将添加到或从文件列表中删除的文件，它将调用此函数，并传入 `lpFileName`。`fAddRemove` 标志指示要向列表中添加的新文件或要删除的旧文件。`nStatus` 参数指定了文件的状态。 当插件 SCC 完成添加和删除文件时，它将返回从 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 调用。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` 功能位是必需的 Visual Studio。  
  
## 请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)