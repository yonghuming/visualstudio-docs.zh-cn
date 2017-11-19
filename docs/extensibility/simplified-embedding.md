---
title: "简化嵌入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4315a55b74d938576572b0630f5dca553643a24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="simplified-embedding"></a>简化嵌入
当有父级其文档视图对象 （即，所做的子级） 简化嵌入在编辑器中启用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>接口实现以处理其窗口命令。 简化的嵌入编辑器不能承载活动控件。 在下图显示用于创建编辑器具有简化的嵌入的对象。  
  
 ![图： 简化嵌入编辑器](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
带简化嵌入编辑器  
  
> [!NOTE]
>  在此图中，仅对象的`CYourEditorFactory`创建标准的基于文件的编辑器所需的对象。 如果要创建自定义编辑器，你不要求实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，这是因为你的编辑器可能具有其自己的专用持久性机制。 为非自定义编辑器，但是，你必须这样做。  
  
 实现编辑器创建与简化嵌入的所有接口都包含在`CYourEditorDocument`对象。 但是，若要支持文档数据的多个视图，拆分到单独的数据与视图对象的接口按下表中所示。  
  
|接口|接口的位置|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|视图|提供向父窗口的连接。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|视图|处理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|视图|启用状态栏更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|视图|使**工具箱**项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|数据|文件发生更改时，将发送通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|数据|启用某一文件类型的另存为功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|数据|实现文档持久性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|数据|允许文件更改事件，如重新加载触发的禁止的显示。|