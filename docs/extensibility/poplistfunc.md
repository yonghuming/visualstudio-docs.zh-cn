---
title: "POPLISTFUNC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPDIRLISTFUNC
helpviewer_keywords: POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 281b18d1e4e802646635cfe354355762014ad40e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
此回调提供给[SccPopulateList](../extensibility/sccpopulatelist-function.md) ide 和源代码管理插件用于更新的文件或目录的列表 (还提供给`SccPopulateList`函数)。  
  
 当用户选择**获取**命令在 IDE 中，则 IDE 将显示的所有文件的用户可以获取一个列表框。 遗憾的是，IDE 不知道用户可能会收到; 的所有文件的确切的列表仅插件都有此列表。 如果其他用户将文件添加到源代码管理项目，这些文件应显示在列表中，但 IDE 不知道有关它们的信息。 IDE 来生成它认为用户可以获取文件的列表。 它会向用户显示此列表之前，它调用[SccPopulateList](../extensibility/sccpopulatelist-function.md) `,`提供源代码管理插件可能添加并从列表中删除文件。  
  
## <a name="signature"></a>签名  
 源代码管理插件修改通过调用用下列原型 IDE 实现的函数的列表：  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>参数  
 pvCallerData  
 `pvCallerData`参数由调用方 (IDE) 传递给[SccPopulateList](../extensibility/sccpopulatelist-function.md)。 源代码管理插件应假定有关此参数的内容执行任何操作。  
  
 fAddRemove  
 如果`TRUE`，`lpFileName`是应该添加到文件列表的文件。 如果`FALSE`，`lpFileName`是应从文件列表中删除的文件。  
  
 nStatus  
 状态`lpFileName`(的组合`SCC_STATUS`bits，请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)有关详细信息)。  
  
 lpFileName  
 要添加或从列表中删除的文件名称的目录完整路径。  
  
## <a name="return-value"></a>返回值  
  
|值|描述|  
|-----------|-----------------|  
|`TRUE`|该插件可以继续调用此函数。|  
|`FALSE`|在 IDE 端 （如内存的情况下扩展） 已存在问题。 插件应停止操作。|  
  
## <a name="remarks"></a>备注  
 对于每个源代码管理插件想要将添加到或从文件列表中删除的文件，它会调用此函数，并传入`lpFileName`。 `fAddRemove`标志指示要向列表中添加的新文件或要删除的旧文件。 `nStatus`参数指定了文件的状态。 当插件 SCC 完成添加和删除文件时，它将返回从[SccPopulateList](../extensibility/sccpopulatelist-function.md)调用。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST`功能位，才能使用 Visual Studio。  
  
## <a name="see-also"></a>另请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)