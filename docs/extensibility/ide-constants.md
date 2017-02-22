---
title: "IDE 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE 中错误"
  - "逻辑视图"
  - "错误 [Visual Studio] IDE"
  - "UI 上下文常量"
  - "常量、 Visual Studio IDE"
  - "IDE 中常量"
  - "物理视图"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 常量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.VSConstants> 类提供特定于集成的开发环境 \(IDE\)，仅在标头文件中前面定义的常量。  
  
## 逻辑和物理视图  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序应将此值与传递 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法以获取 **打开** 对话框中，在这种情况下，在可能的代码视图。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序会传递此值与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法以获取 **打开** 对话框中，在这种情况下填充可能 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> 调试映射到同一个视图作为视图 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序会传递此值与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法以获取 **打开** 对话框中，在这种情况下 **视图窗体** 设计器视图。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序会传递此值与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法以获取 **打开** 对话框中，在这种情况下编辑器工厂的默认\/主视图。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序会传递此值与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法以获取 **打开** 对话框中，在该工作的文档或数据的文本编辑器视图。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 处理程序会传递此值与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，该对话框将提示用户选择要使用的用户定义的视图。|  
  
## 编辑器工厂标志  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|已过时的标志的第一个参数为按位组合 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|作为第一个参数的按位组合 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, ，方法中，这表示编辑器工厂应执行必需的修复。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|作为第一个参数的按位组合 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法，此标志是互斥的 exclusive 的 <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|作为第一个参数的按位组合 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法，这表示编辑器工厂应创建编辑器中，而不显示用户界面 \(UI\)。|  
  
## Visual Studio 错误  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|常量由接口返回到异步行为时所述，在对象已经忙|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 为"兼容的文档数据"。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"未加载的包。"|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和该异常指示"已存在项目。"|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"项目配置失败。"|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"未加载的项目。"|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"已打开解决方案"。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"未打开解决方案"。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|返回具有指定从一个字符串数组的参数的生成接口 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> 界面，但该实现可以只将方法应用于所有输出。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法返回此值，如果该文档具有一种格式，不能在编辑器中打开。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值，该值指示在用户单击中的后退按钮 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 向导。|  
  
## Visual Studio 常量  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|错误 HRESULT 是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，指示"项目转发。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|一个常量，它是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 为"工具箱标记"。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|一个常量，它是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以便为广播一条通知消息通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 指示模态的开头的方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|一个常量，它是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以便为广播一条通知消息通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 指示模态的结尾处的方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|一个常量，它是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以便为广播一条通知消息通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> ，该值指示命令栏度量值已更改的方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|一个常量，它是特定于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，该值指示尚未设置 cookie。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 表示项目项不存在的项标识符。 当前没有选定内容时，使用此值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 表示项目层次结构的根，用于标识整个层次结构，而不是单个项的项标识符。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 表示当前所选的一个或多个项目，其中可包括层次结构的根的项标识符。|  
  
## IVsSelectionEvents  
 描述在 IDE 的哪个组件只是选择了，在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 调用，例如。  
  
|返回的常量|值|  
|-----------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## VSSELELEMID  
 用于指示新的选择状态的常量。  
  
|返回的常量|值|  
|-----------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## 组件选择器对话框常量  
  
|返回的常量|值|  
|-----------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER 1280 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER 1281 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER 1290 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER 1287 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER 1285 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER 1288 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER 1286 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER 1289 \+|  
  
## 请参阅  
 [IDE 定义用于扩展项目系统的命令](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)