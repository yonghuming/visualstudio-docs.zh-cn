---
title: "源控件的设计决策 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320a8013177d44491470f8f55c8ee3e1fb19501c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-design-decisions"></a>源控件的设计决策
实现源代码管理时，以下设计决策应考虑的项目。  
  
## <a name="will-information-be-shared-or-private"></a>信息是否会使用共享或私有？  
 最重要的设计决策，你可以在哪些信息是可共享，什么是私有。 例如，共享的项目文件的列表，但在此列表中的文件，有些用户可能想要的专用文件。 共享编译器设置，但通常私有启动项目。 设置为纯粹共享、 共享的替代方法，或只是私有。 按照设计，专用的项，如解决方案用户选项 (.suo) 文件未签入到[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。 请务必在如.suo 文件中或你创建，例如，特定的私有文件的专用文件中存储任何隐私信息。 csproj.user 文件对于 Visual C# 或。 适用于 Visual Basic vbproj.user 文件。  
  
 此决策不是完全内包含，可以对逐个项的项的方式进行。  
  
## <a name="will-the-project-include-special-files"></a>将该项目包括特殊文件？  
 另一个重要设计决策是项目结构是否使用特殊文件。 特殊文件是隐藏的文件生成可见在解决方案资源管理器和签入和签出对话框中的文件。 如果你使用特殊文件，请遵循以下准则：  
  
1.  未将特殊文件与项目根节点-也就是说，与项目文件本身。 你的项目文件必须是单个文件。  
  
2.  当添加、 删除或重命名在项目中，相应特殊文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>必须带有标记集，该值指示文件是特殊文件触发事件。 这些事件由响应调用相应的项目中的环境<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法。  
  
3.  当你的项目或编辑器调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>对于文件，与该文件相关联的特殊文件未自动签出。传递以及父文件中的特殊文件。 环境将检测所有传入的文件之间的关系，并相应地隐藏签出 UI 中的特殊文件。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [支持源代码管理](../../extensibility/internals/supporting-source-control.md)