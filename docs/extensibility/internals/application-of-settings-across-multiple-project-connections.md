---
title: "跨多个项目连接设置的应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9750d946a941e86a6c0a6973661f00f8f44cf9b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>跨多个项目连接设置的应用程序
源代码管理插件生成使用源控件的插件 API 1.2 中，可以使用批处理操作来执行相同的源代码管理操作跨多个项目或多个连接上下文。 批处理可以用于消除冗余，每个项目中的用户体验的对话框。  
  
 如果用户选择了属于在源代码管理插件的多个连接使用源控件插件 API 1.1 （例如，在不同的文件共享计算机上两个 Web 项目） 生成的多个项，并检查其，用户将看到相同的对话框中重复。 发生这种情况是即使用户单击**应用于所有**复选框在对话框中，因为 IDE 重置其状态为每个连接上下文。  
  
## <a name="new-capability-flag"></a>新功能标志  
 `SccBeginBatch`函数集`SCC_CAP_BATCH`标志以指示批处理操作正在进行  
  
## <a name="new-functions"></a>新的函数  
 以下新功能支持批处理操作：  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`函数开始源代码管理操作的组。 `SccEndBatch`关闭组。 不能嵌套组。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)