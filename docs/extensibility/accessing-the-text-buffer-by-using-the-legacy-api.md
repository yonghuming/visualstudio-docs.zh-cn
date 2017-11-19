---
title: "通过使用旧版 API 访问文本缓冲区 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: facfc1670bf9d04035beffc47b7124bd5d309a7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>通过使用旧版 API 访问文本缓冲区
文本负责管理文本流和文件持久性。 尽管缓冲区可以读取或写入其他格式，使用 Unicode 执行所有普通通信使用的缓冲区。 在旧的 Api 中，文本缓冲区可以使用一维或二维的坐标系统以标识缓冲区中的字符位置。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>一个和两个维度协调系统  
 一维的坐标位置开始算起，如 147 时缓冲区中从第一个字符的字符的位置。 你使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>接口来访问缓冲区中的一维位置。 二维的坐标系统基于行和索引对。 例如，在 43 缓冲区中的字符，5 将出现在上行 43，在这一行中的第一个字符右侧的五个字符。 访问在缓冲区中使用的二维位置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>接口。 同时<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>接口实现的文本缓冲区对象 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>)，并且可以通过使用从相互访问`QueryInterface`。 下图显示了这些和其他密钥接口上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 ![文本缓冲区对象](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文本缓冲区对象  
  
 尽管任一坐标系文本缓冲区中工作，但它被优化为使用二维坐标。 一维坐标系可以创建的性能开销。 因此，使用尽可能二维坐标系统。  
  
 文本缓冲区的第二个职责是文件持久性。 若要执行此操作，该文本缓冲区对象实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>并且可作为项目项的文档数据对象组件，并且涉及在持久性中其他环境组件。 有关详细信息，请参阅[打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [通过使用旧版 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 说明如何更改视图设置，请使用旧的 API。  
  
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 说明如何使用文本管理器来监视全局设置...  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)