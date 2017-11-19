---
title: "如何： 更新状态栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6218d697880da3ebf0d9af5599b5a7ca37ddf2f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-the-status-bar"></a>如何： 更新状态栏
**状态栏**控件条位于包含一个或多个状态文本行或指示器的许多应用程序窗口底部。  
  
### <a name="to-update-the-status-bar"></a>更新状态栏  
  
1.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>提供你的编辑器，如窗体视图和代码视图的每个单独的视图对象 (DocView)。  
  
2.  当 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>，更新中的信息**状态栏**通过调用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>。  
  
    > [!NOTE]
    >  IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>仅当你的文档窗口最初已激活。 对于文档窗口处于活动状态的时间的其余部分中，你必须更新**状态栏**作为编辑器更改的状态的信息。  
  
## <a name="robust-programming"></a>可靠编程  
 A**状态栏**包含四个单独的字段：  
  
-   状态文本  
  
-   进度栏  
  
-   动画的图标  
  
-   编辑器信息  
  
 有关详细信息，请参阅[状态栏](/cpp/mfc/status-bars)。  
  
 IDE 将自动调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法你<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>实现激活你的文档窗口时。  
  
 VSPackage 实施者负责更新状态栏中的状态文本。 IDE 重置此字符串为"就绪"，如果状态文本字段设置为空文本 ("") 在空闲时间。  
  
## <a name="see-also"></a>另请参阅  
 [状态栏](/cpp/mfc/status-bars)