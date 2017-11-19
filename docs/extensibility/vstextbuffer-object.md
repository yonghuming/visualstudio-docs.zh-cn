---
title: "VSTextBuffer 对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d25551d6af9b2250275713541dc9c9df39ca90ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 对象
文本缓冲区对象表示的 Unicode 文本，通常与文件相关的流。 A<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象可使用上下文之外的核心编辑器中，如向导。  
  
 下表显示的接口`VSTextBuffer`。  
  
|方法|描述|  
|------------|-----------------|  
|[不需要此行为](http://msdn.microsoft.com/library/windows/desktop/ms683797)|标准 OLE 接口。 主要用于处理在缓冲区中撤消/重做。|  
|[为 IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|标准 OLE 接口。|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|允许复合词操作 （即，在单个撤消/重做单元进行分组的操作） 的创建。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|启用管理的文本缓冲区的文档数据的持续的性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服务; 示例：由多个客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用于搜索缓冲区。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供读取和写入使用二维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供读取和写入使用一维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 面向流的、 按顺序访问缓冲区中的文本。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供对属性的泛型集合的访问。 最重要的属性是名称或标记时的缓冲区。 通过创建 GUID 并将其作为一个键，可以将自己的随机数据存储在具有此接口的缓冲区。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|事件支持连接点。|  
  
## <a name="remarks"></a>备注  
 `VSTextBuffer`通常通过找到`QueryInterface`上调用`IVsTextBuffer`。 有关详细信息，请参阅[文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [数字编辑](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)