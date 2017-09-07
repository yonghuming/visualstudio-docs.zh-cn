---
title: "创建核心编辑器和注册编辑器文件类型 |Microsoft 文档\""
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: dec3e53df108377dacfc53ba308029933654b789
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>演练： 创建核心编辑器和注册编辑器文件类型
本演练演示如何创建启动 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器具有.myext 文件扩展名的文件时将会加载。  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 包项目模板的位置  
 可在“新建项目”  对话框中的三个不同位置找到 Visual Studio 包项目模板：  
  
1.  在“Visual Basic 扩展性”之下。 项目的默认语言为 Visual Basic。  
  
2.  在“C# 扩展性”之下。 项目的默认语言为 C#。  
  
3.  在“其他项目类型扩展性”之下。 项目的默认语言为 C++。  
  
### <a name="to-create-the-vspackage"></a>若要创建 VSPackage  
  
-   启动[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]并创建[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]名为的 VSPackage `MyPackage`、 中所述[演练： 创建菜单命令 VSPackage](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32)。  
  
### <a name="to-add-the-editor-factory"></a>若要添加编辑器工厂  
  
1.  右键单击**MyPackage**项目，指向**添加**，然后单击**类**。  
  
2.  在**添加新项**对话框框中，请确保**类**选择模板，类型`EditorFactory.cs`作为名称，然后单击**添加**将类添加到你的项目。  
  
     应自动打开 EditorFactory.cs 文件。  
  
3.  在代码中引用以下程序集。  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  添加到 GUID`EditorFactory`类通过添加`Guid`紧靠类声明的属性。  
  
     你可以通过使用 guidgen.exe 程序在生成新的 GUID[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的命令提示符，或通过单击**创建 GUID**上**工具**菜单。 此处使用的 GUID 只是一个示例;不要在你的项目中使用它。  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  在类定义中，添加两个私有变量，使其包含父包和服务提供程序。  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  添加一个公共类构造函数采用一个类型的参数<xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  修改`EditorFactory`类声明为派生自<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口。  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  右键单击<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>，单击**实现接口**，然后单击**显式实现接口**。  
  
     这将添加必须中实现的四个方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口。  
  
9. 将 `IVsEditorFactory.Close` 方法的内容替换为以下代码。  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 内容替换`IVsEditorFactory.SetSite`替换为以下代码。  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. 将 `IVsEditorFactory.MapLogicalView` 方法的内容替换为以下代码。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. 将 `IVsEditorFactory.CreateEditorInstance` 方法的内容替换为以下代码。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. 编译该项目，并确保没有任何错误。  
  
### <a name="to-register-the-editor-factory"></a>若要注册编辑器工厂  
  
1.  在**解决方案资源管理器**，双击 Resources.resx 文件以打开到在其中的字符串表条目**String1 是**选。  
  
2.  更改到的标识符名称`IDS_EDITORNAME`和到文本**MyPackage 编辑器。** 此字符串将显示为你的编辑器的名称。  
  
3.  打开 VSPackage.resx 文件并添加一个新字符串，将名称设置为**101**和值的`IDS_EDITORNAME`。 这将包提供的资源 ID 访问你刚刚创建的字符串。  
  
    > [!NOTE]
    >  如果 VSPackage.resx 文件包含另一个字符串`name`属性设置为**101**，替换另一个唯一的数字值，在此处以及以下步骤中。  
  
4.  在**解决方案资源管理器**，打开 MyPackagePackage.cs 文件。  
  
     这是主包文件。  
  
5.  之前添加以下用户特性`Guid`属性。  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>属性.myext 文件扩展名将与相关联编辑器工厂，以便任何时候，只要具有加载扩展插件、 调用编辑器工厂的文件。  
  
6.  添加到一个私有变量`MyPackage`类之前构造函数中，并为其提供类型`EditorFactory`。  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  查找`Initialize`方法 (你可能需要打开`Package Members`隐藏的区域) 的调用后添加以下代码和`base.Initialize()`。  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  编译此程序，并确保没有任何错误。  
  
     此步骤在实验注册表配置单元中注册的编辑器工厂[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如果系统提示你重写 resource.h 文件时，请单击**确定**。  
  
9. 创建一个名为 TextFile1.myext 的示例文件。  
  
10. 按**F5**打开的实验实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
11. 在实验性[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]上**文件**菜单上，指向**打开**，然后单击**文件**。  
  
12. 查找 TextFile1.myext，然后单击**打开**。  
  
     现在应加载的文件。  
  
## <a name="robust-programming"></a>可靠编程  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器处理大量的基于文本的文件类型和与语言服务以提供一组丰富的功能，如语法突出显示，大括号匹配和 IntelliSense 单词完成和成员完成列表紧密协作。 如果你正在使用基于文本的文件，你可以使用以及自定义语言服务支持你的特定文件类型核心编辑器。  
  
 VSPackage 可以调用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器通过提供编辑器工厂。 加载与之关联的文件的任何时候都可以使用此编辑器工厂。 如果文件是项目的一部分，核心编辑器自动被调用除非通过你的 VSPackage 中重写。 但是，如果在项目外部加载的文件，然后核心编辑器必须显式调用由你的 VSPackage。  
  
 有关核心编辑器的详细信息，请参阅[内核心编辑器](../extensibility/inside-the-core-editor.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [使用旧版 API 实例化核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
