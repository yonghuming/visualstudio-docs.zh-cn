---
title: "属性窗口字段和接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4dd37d33230be758bd5a5adf6f5e10d5a978800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
选择以确定在显示的信息的模型**属性**窗口开始算起在 IDE 中具有焦点的窗口。 每个窗口中和中所选的窗口中，对象只能有推送到全局选择上下文其选择上下文对象。 该窗口拥有焦点时，环境窗口框架中的值更新全局选择上下文。 当焦点更改时，因此会选择上下文。  
  
## <a name="tracking-selection-in-the-ide"></a>跟踪在 IDE 中的选定内容  
 窗口框架或站点时，拥有由 IDE、 具有一个称为服务<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 以下步骤演示了如何更改引起的用户将焦点更改为另一个打开的窗口或选择不同的项目项中所选内容中**解决方案资源管理器**，实现更改中显示的内容**属性**窗口。  
  
1.  由你放置在所选的窗口调用中的 VSPackage 创建的对象<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>能够<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>调用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  选择容器，提供所选的窗口中，创建其自己<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>对象。 当选择会有所变化，VSPackage 调用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>通知任何侦听器在环境中，包括**属性**更改窗口。 它还提供对与新的选择相关的层次结构和项信息的访问。  
  
3.  调用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>并将其传递中的所选层次结构项`VSHPROPID_BrowseObject`参数填充<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>对象。  
  
4.  一个对象派生自[IDispatch 接口](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)为返回<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>项请求，并且环境包装到<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>（请参阅下面的步骤）。 如果调用失败，环境将第二个调用`IVsHierarchy::GetProperty`，将其传递选择容器<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>或多个层次结构项目提供。  
  
     你的项目不会创建 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因为环境提供窗口 VSPackage，实现它 (例如，**解决方案资源管理器**) 构造<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代表它。  
  
5.  环境调用的方法<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>若要获取基于的对象`IDispatch`接口来填充**属性**窗口。  
  
 在值时**属性**窗口发生更改时，Vspackage 实现`IVsTrackSelectionEx::OnElementValueChangeEx`和`IVsTrackSelectionEx::OnSelectionChangeEx`要报告给此元素的值的更改。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>中显示的信息保持**属性**窗口同步具有的属性值。 有关详细信息，请参阅[属性窗口中更新属性值](#updating-property-values-in-the-properties-window)。  
  
 除了选择其他项目项中**解决方案资源管理器**若要显示与该项相关的属性，你还可以选择从使用下拉列表上可用的窗体或文档窗口内的不同对象**属性**窗口。 有关详细信息，请参阅[属性窗口对象列表](../../extensibility/internals/properties-window-object-list.md)。  
  
 你可以更改中显示信息的方式**属性**窗口网格中按字母顺序排列为分类，并且，如果可用，则还可以通过单击上的相应按钮来打开所选对象的属性页**属性**窗口。 有关详细信息，请参阅[属性窗口按钮](../../extensibility/internals/properties-window-buttons.md)和[属性页](../../extensibility/internals/property-pages.md)。  
  
 最后，底部**属性**窗口也包含在所选的字段的说明**属性**窗口网格。 有关详细信息，请参阅[从属性窗口中获取字段说明](#getting-field-descriptions-from-the-properties-window)。  
  
## <a name="updating-property-values-in-the-properties-window"></a>属性窗口中更新属性值
有两种方法可以保持“属性”  窗口与属性值更改同步。 第一种是调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>接口，从而提供对基本窗口化功能，包括访问和创建由环境提供的工具和文档窗口的访问。 下面的步骤介绍了此同步过程。  
  
### <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新属性值  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 接口更新属性值  
  
1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(通过<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服务) 任何时候，只要 Vspackage、 项目，或编辑器需要创建或枚举工具或文档窗口。  
  
2.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保留**属性**窗口与项目的属性更改同步 (或浏览的任何其他所选对象**属性**窗口) 而无需实现<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>并触发<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>事件。  
  
3.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>建立并禁用，分别，而无需层次结构的层次结构事件的客户端通知，以实现<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
### <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新属性值  
 第二种保持“属性”  窗口与属性值更改同步的方法是，实现可连接对象上的 `IConnection` ，以指示输出接口是否存在。 如果你想要本地化的属性名称，派生对象从<xref:System.ComponentModel.ICustomTypeDescriptor>。 <xref:System.ComponentModel.ICustomTypeDescriptor>实现可以修改它将返回的属性说明符和更改的属性名称。 若要本地化说明，创建派生自的属性<xref:System.ComponentModel.DescriptionAttribute>并重写 Description 属性。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>实现 IConnection 接口的注意事项  
  
1.  `IConnection`提供对使用的枚举器子对象的访问<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>接口。 它还提供访问所有连接点子对象，它实现的每个<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>接口。  
  
2.  任何浏览对象都负责实现<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>事件。  “属性”窗口通过 `IConnection`为事件集提供建议。  
  
3.  连接点，来控制在其实现它允许多少连接 （一个或多个） <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>。 只允许一个接口的连接点可返回<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>从<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>方法。  
  
4.  客户端可以调用`IConnection`接口，以获得对使用的枚举器子对象的访问<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>接口。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>接口然后，可以调用要枚举连接点的每个输出接口 ID (IID)。  
  
5.  `IConnection`此外可以调用以获取连接点使用的子对象的访问权限<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>每个输出 IID 的接口。 通过<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>接口，客户端启动或终止与可连接对象和客户端自己的同步的通知循环。客户端还可以调用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>接口，以获得与的枚举器对象<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>接口，它就会了解有关对连接进行枚举。  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>从属性窗口中获取字段说明
在“属性”  窗口底部，说明区域显示了与所选属性字段相关的信息。 默认情况下此功能处于开启状态。 如果你想要隐藏说明字段，右键单击“属性”  窗口并单击“说明” 。 执行此操作还会删除“菜单”窗口中“说明”  标题旁的复选标记。 你可以按照将“说明”  切换回开启状态的步骤来再次显示该字段。  
  
 说明字段中的信息来自<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每个方法、接口、组件类等在类型库中均可拥有一个未本地化的 `helpstring` 特性。 **属性**窗口检索中的字符串<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>。  
  
### <a name="to-specify-localized-help-strings"></a>指定本地化的帮助字符串  
  
1.  将 `helpstringdll` 特性添加到类型库中的库语句（`typelib`）。  
  
    > [!NOTE]
    >  如果类型库位于对象库 (.olb) 文件中，则此步骤是可选的。  
  
2.  为字符串指定 `helpstringcontext` 特性。 你还可以指定 `helpstring` 特性。  
  
     这些特性不同于包含在实际 .chm 文件帮助主题中的 `helpfile` 和 `helpcontext` 特性。  
  
 若要检索为突出显示的属性名称中，显示的说明信息**属性**窗口调用<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>选择的属性，指定所需`lcid`属性，则为输出字符串。 在内部，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>查找中指定的.dll 文件`helpstringdll`属性和调用`DLLGetDocumentation`上使用指定的上下文该.dll 文件和`lcid`属性。  
  
 `DLLGetDocumentation` 的签名和实现为：  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` 函数必须是在 .def 文件中为 DLL 定义的导出。  
  
 在内部，会创建一个实际为 DLL 的 .olb 文件。 此 DLL 包含一个资源（类型库 (.tlb) 文件）和一个导出的函数（ `DLLGetDocumentation`）。  
  
 就 .olb 文件而言， `helpstringdll` 特性是可选的，因为它是包含 .tlb 文件本身的同一文件。  
  
 若要获取显示在“说明”  窗格中的字符串，为此你至少需要在类型库中指定 `helpstring` 特性。 如果你希望本地化这些字符串，则必须指定 `helpstringdll` （可选）特性和 `helpstringcontext` （必需）特性，并实现 `DLLGetDocumentation`。  
  
 通过 idl 的 `helpstringcontext` 特性和 `DLLGetDocumentation`获取本地化的信息时，没有需要实现的其他接口。  
  
 获取本地化的名称和属性说明的另一种是通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 与此方法的实现相关的详细信息，请参阅[属性窗口字段和接口](../../extensibility/internals/properties-window-fields-and-interfaces.md)。  

## <a name="see-also"></a>另请参阅  
 [扩展属性](../../extensibility/internals/extending-properties.md)