---
title: "简化的嵌入 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的简单查看嵌入"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 简化的嵌入
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

简化的嵌入在编辑器中启用，其文档视图对象父 \(即提交子级\) 时 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，并且， <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 接口实现处理其窗口的命令。  简化嵌入编辑不能承载活动控件。  使用的对象的简化的嵌入创建编辑如下图所示。  
  
 ![图：简化的嵌入式编辑器](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
与简化的嵌入的编辑  
  
> [!NOTE]
>  此图中的对象，只需要 `CYourEditorFactory` 对象创建标准的基于文件的编辑器。  如果创建自定义编辑器，不需要实现， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，因为编辑器可以将其自己的私有保持机制。  对于非自定义编辑器，但是，您必须这样做。  
  
 实现的任何接口用简化的嵌入创建编辑器在 `CYourEditorDocument` 对象包含。  但是，支持多视图文档数据，如下表所示可在单独的数据和视图对象上的接口。  
  
|接口|接口的位置|使用|  
|--------|-----------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|视图|提供连接到父窗口。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|视图|处理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|视图|启用状态栏更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|视图|启用 **工具箱** 项目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|数据|，在文件发生更改时，通知发送。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|数据|启用另存为文件类型的函数。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|数据|启用文档的持久性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|数据|允许文件更改事件禁止，如重新加载触发。|