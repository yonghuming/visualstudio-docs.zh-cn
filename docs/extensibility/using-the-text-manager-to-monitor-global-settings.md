---
title: "使用文本管理器来监视全局设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9687e4f0be16fb42f13c6f9dd20a2cb39be50cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>使用文本管理器来监视全局设置
如果实现核心编辑器，你必须监视对全局设置，进行更改，因为这些更改可能影响你的编辑器实例。 你可以通过侦听由文本管理器引发的事件跟踪所做的更改。 例如，在核心编辑器中，例如其文档数据对象，指定的外观或行为的一个组件的全局首选项时的文本管理器将存储此信息，并将其传递给受影响的所有客户端。  
  
## <a name="text-manager-functions"></a>文本管理器函数  
 文本管理器引发大量设置，包括以下的事件：  
  
-   缓冲区是否受源代码管理  
  
-   如何注册文件更改通知  
  
-   如何跟踪哪些视图是与某些缓冲区关联的  
  
-   文本着色首选项  
  
-   空间首选项与选项卡  
  
 是唯一的给定语言的首选项不受文本管理器。 必须由每个语言服务管理这些设置。  
  
 文本管理器的事件通知由<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>接口。 实现此接口上你的客户端对象以处理事件引发的文本管理器。 通过使用这些事件注册<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文本管理器上的接口。  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [编辑器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)