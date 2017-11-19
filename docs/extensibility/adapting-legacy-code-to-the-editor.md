---
title: "调整到编辑器的旧代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03c0cbd20258618297e943524d06ba7b3a496264
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adapting-legacy-code-to-the-editor"></a>调整到编辑器的旧代码
Visual Studio 编辑器具有许多功能，你可以从现有代码组件访问。 下面的说明演示如何改编非 MEF 组件，例如，VSPackage，使用编辑器功能。 说明还演示如何使用适配器来托管和非托管代码中获取的编辑器中的服务。  
  
## <a name="editor-adapters"></a>编辑器适配器  
 此外公开的类和接口中的编辑器对象的包装编辑器适配器或填充码，则<xref:Microsoft.VisualStudio.TextManager.Interop>API。 你可以使用例如移动非编辑器服务之间的适配器、 Visual Studio shell 命令和编辑器服务。 （这是编辑器 Visual Studio 中的当前承载方式。）适配器还启用旧的编辑器和语言服务扩展在 Visual Studio 中正常工作。  
  
## <a name="using-editor-adapters"></a>使用编辑器适配器  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>提供新的编辑器接口和旧的接口，之间切换的方法和还创建适配器的方法。  
  
 如果某一 MEF 组件部分中将此服务，可以将服务导入，如下所示。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 如果你想要在非 MEF 组件使用此服务，请按照本主题后面的"使用 Visual Studio 编辑器服务中非 MEF 组件"一节中的说明。  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>新的编辑器 API 和旧版 API 之间切换  
 使用以下方法编辑器对象和旧版的接口之间进行切换。  
  
|方法|转换|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|将转换<xref:Microsoft.VisualStudio.Text.ITextBuffer>到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|将转换<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>到<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|将转换<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>到<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|将转换<xref:Microsoft.VisualStudio.Text.Editor.ITextView>到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|将转换<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>到<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
  
## <a name="creating-adapters"></a>创建适配器  
 使用以下方法来创建旧接口适配器。  
  
|方法|转换|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|创建<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>指定<xref:Microsoft.VisualStudio.Utilities.IContentType>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|创建<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>为<xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>在非托管代码中创建适配器  
 所有适配器类都注册是在本地可共同创建，可以通过实例化`VsLocalCreateInstance()`函数。  
  
 通过使用 vsshlids.h 文件中定义的 Guid 创建所有适配器...\VisualStudioIntegration\Common\Inc\ Visual Studio SDK 安装文件夹。 若要创建 VsTextBufferAdapter 的实例，使用下面的代码。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>在托管代码中创建适配器  
 在托管代码中，你可以共同创建适配器，所述的非托管代码的方式相同。 你还可以使用 MEF 允许的服务，你可以创建并与适配器进行交互。 获取一个适配器的这种方式使更细化的控制数量超过拥有的共同创建时。  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>若要为 IVsTextView 创建适配器  
  
1.  添加对 Microsoft.VisualStudio.Editor.dll 的引用。 请确保`CopyLocal`设置为`false`。  
  
2.  实例化<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>、，如下所示。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  调用 `CreateX()` 方法。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>使用 Visual Studio 编辑器中直接从非托管代码  
 Microsoft.VisualStudio.Platform.VSEditor 命名空间和 Microsoft.VisualStudio.Platform.VSEditor.Interop 命名空间作为 IVx * 接口公开 COM 可调用的接口。 例如，Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer 接口是 COM 版本的<xref:Microsoft.VisualStudio.Text.ITextBuffer>接口。 从`IVxTextBuffer`，可以有权访问缓冲区快照、 修改缓冲区、 侦听对缓冲区的文本更改事件和创建跟踪点和跨度。 下面的步骤演示如何访问`IVxTextBuffer`从`IVsTextBuffer`。  
  
#### <a name="to-get-an-ivxtextbuffer"></a>若要获取 IVxTextBuffer  
  
1.  IVx * 接口的定义位于 VSEditor.h 文件...\VisualStudioIntegration\Common\Inc\ Visual Studio SDK 安装文件夹。  
  
2.  通过使用下面的代码实例化的文本缓冲区`IVsUserData->GetData()`方法。 在下面的代码中，`pData`是一个指向`IVsUserData`对象。  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>在非 MEF 组件中使用 Visual Studio 编辑器中服务  
 如果你有现有的托管的代码组件，如果不使用 MEF，并且你想要使用 Visual Studio 编辑器中的服务，你必须添加对包含 ComponentModelHost VSPackage 的程序集的引用，并获取其 SComponentModel 服务。  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>若要使用来自非 MEF 组件的 Visual Studio 编辑器组件  
  
1.  添加对中的 Microsoft.VisualStudio.ComponentModelHost.dll 程序集的引用...Visual Studio 安装 \Common7\IDE\ 文件夹。 请确保`CopyLocal`设置为`false`。  
  
2.  添加一个私有`IComponentModel`到想要使用 Visual Studio 编辑器服务，如下所示的类的成员。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  实例化组件初始化方法中的组件模型。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  此后中,，你可以获取任何一种 Visual Studio 编辑器服务通过调用`IComponentModel.GetService<T>()`所需的服务的方法。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```