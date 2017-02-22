---
title: "VSTextBuffer 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextBuffer"
helpviewer_keywords: 
  - "VSTextBuffer object 参考"
  - "视图 [Visual Studio SDK]，VSTextBuffer 对象"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# VSTextBuffer 对象
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本缓冲区对象表示 Unicode 文本，通常与文件相关联的流。 一个 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 可以如向导的核心编辑器上下文之外使用对象。  
  
 下表显示了接口的 `VSTextBuffer`。  
  
|方法|描述|  
|--------|--------|  
|[不需要此行为](http://msdn.microsoft.com/library/windows/desktop/ms683797)|标准 OLE 接口。 主要用于处理在缓冲区中撤消\/重做。|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|标准 OLE 接口。|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|标准 OLE 接口。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以创建复合音操作 \(即单个撤消\/重做单位进行分组的操作\)。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|使文本缓冲区由管理的文档数据的持久性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服务;由多个客户端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用来搜索一个缓冲区。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供了读取和写入使用二维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供了读取和写入使用一维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 面向流的、 按顺序访问缓冲区中的文本。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供对属性的泛型集合的访问。 最重要属性是缓冲区的名称或的名字对象。 通过创建 GUID 并使用它作为键，可以在具有此接口的缓冲区中存储您自己的随机数据。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支持连接点事件。|  
  
## 备注  
 `VSTextBuffer` 通常通过找到 `QueryInterface` 调用 `IVsTextBuffer`。 有关详细信息，请参阅 [文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/zh-cn/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)