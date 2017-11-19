---
title: "旧语言服务模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afc15ea50921b1feca34a8b305c5028979a0d1ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="model-of-a-legacy-language-service"></a>旧语言服务模型
语言服务定义的元素和特定语言的功能，用于提供对该语言的特定信息的编辑器。 例如，编辑器需要知道的元素和语言关键字，才能支持语法突出显示。  
  
 语言服务紧密配合由编辑器和包含编辑器中的视图的文本缓冲区。 Microsoft IntelliSense**快速信息**选项是由语言服务提供的功能的示例。  
  
## <a name="a-minimal-language-service"></a>最小语言服务  
 最基本的语言服务包含以下两个对象：  
  
-   *语言服务*实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>接口。 语言服务具有的语言，包括其名称、 文件扩展名，代码窗口管理器中和着色器的信息。  
  
-   *着色器*实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>接口。  
  
 下面的概念图显示了基本语言服务模型。  
  
 ![语言服务模型图](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本语言服务模型  
  
 文档窗口承载*文档视图*的编辑器中，在此情况下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心编辑器。 由编辑器中拥有文档视图和文本缓冲区。 这些对象使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过专门的文档窗口调用*代码窗口*。 中包含代码窗口<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>创建并由 IDE 控制对象。  
  
 加载给定扩展名的文件后，编辑器定位该扩展与关联的语言服务并将传递给它的代码窗口通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。 语言服务返回*代码窗口管理器*，该类实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>接口。  
  
 下表概述了在模型中的对象。  
  
|组件|对象|函数|  
|---------------|------------|--------------|  
|文本缓冲区|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode 读/写文本流。 很可能要使用其他编码的文本。|  
|“代码”窗口|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|文档窗口，其中包含一个或多个文本视图。 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是在多文档界面 (MDI) 模式下，代码窗口是 MDI 子窗体。|  
|文本视图|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|窗口可让用户导航并通过使用键盘和鼠标查看文本。 作为一个编辑器，向用户显示的文本视图。 您可以使用普通的编辑器窗口、 输出窗口和即时窗口中的文本视图。 此外，你可以配置代码窗口中的一个或多个文本视图。|  
|文本管理器|由<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服务，无法获取的其中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>指针|维护由前面所述的所有组件共享的通用信息的组件。|  
|语言服务|依赖于; 实现实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|一个对象，提供特定于语言的信息，如语法突出显示、 语句完成和大括号匹配的编辑器。|  
  
## <a name="see-also"></a>另请参阅  
 [自定义编辑器中的文档数据和文档视图](../../extensibility/document-data-and-document-view-in-custom-editors.md)