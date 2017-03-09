---
title: "使用选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具选项页 [Visual Studio SDK]，使用情况"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# 使用选项页
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动化模型提供了 <xref:EnvDTE.DTE> 对象，以允许 VSPackage 访问在“工具”菜单上的“选项”对话框。  
  
 通常情况下，无论“选项”对话框中的页是由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 提供的，还是由 VSPackage 提供的，都可以通过使用自动化模型来访问它们。 但是，有例外情况，如下所示：  
  
-   无法以编程方式访问“动态帮助”页的设置。 可通过使用自动化模型控制“动态帮助”功能，但是必须在代码中直接完成控制。 有关详细信息，请参阅[How to: Control the Dynamic Help Window](http://msdn.microsoft.com/zh-cn/7f5777aa-c270-4058-a175-8ce8a4ed25eb)。  
  
-   “字体和颜色”页面设置的控制通过其自身 API 提供，而非通过自动化模型提供。 有关更多信息，请参见[使用字体和颜色](../extensibility/using-fonts-and-colors.md)。  
  
-   不能通过自动化模型获得特定于语言的属性。  
  
 受到查询时，不支持 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动化模型的“选项”页可能不会返回自动化 <xref:EnvDTE.Properties> 集合。 如果返回了集合，并非所有功能都存在。 有关如何管理这些功能的更多信息，请参阅[DTE 属性集合](../Topic/DTE%20Properties%20Collections.md)。  
  
## 管理选项页  
 若要管理“选项”页，VSPackage 必须从自动化模型获取 <xref:EnvDTE.DTE> 对象。  
  
> [!NOTE]
>  当 VSPackage 使用自动化模型来查询和更改已安装的“选项”页上的设置时，它不会扩展 IDE 功能。 因此，包不必实现自动化对象。  
  
 若要通过自动化模型获取 <xref:EnvDTE.DTE> 对象，调用 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法并提供 `SID_SDTE` 的服务 ID 参数和 `IID__DTE` 的接口参数，如下所示。  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 若要通过使用 Managed Package Framework \(MPF\) 获取 <xref:EnvDTE.DTE> 对象，调用 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 方法，并提供类型 <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> 的 `serviceType` 参数。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 由两个标识符指定“选项”页。 第一个标识符是一个字符串，指示包含“选项”页的文件夹。 第二个标识符是一个字符串，指示文件夹中的特定项。 这些被称为“选项”页的类别和子类别，或者其主题和子主题。  
  
 例如，用于处理 Basic 代码的文本编辑器设置在导航窗格中，作为文本编辑器文件夹的“Basic”成员。 该类别的标识符为 `TextEditor`，其子类别为 `Basic`，且“选项”页本身被称为 `TextEditor.Basic` 页。  
  
> [!NOTE]
>  由于本地化和其他原因，在“选项”页上显示的名称可能与用作类别和子类别标识符的字符串不同。 如果标识符未记录在其他位置，你可能必须使用自动化来查询 IDE 以获得正确的标识符。 注册表位置是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS Version\>*\\AutomationProperties，其中 *\<VS Version\>* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本的版本号。 有关更多信息，请参见[注册自定义选项页](../misc/registering-custom-options-pages.md)。  
  
 你可以通过使用以下示例通过自动化模型获取 `TextEditor.Basic` 页面的属性。  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 若要通过使用 MPF 获取属性，使用 <xref:EnvDTE._DTE.Properties%2A> 方法。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 <xref:EnvDTE.Properties.Item%2A> 方法从作为 <xref:EnvDTE.Property> 对象的 <xref:EnvDTE.Properties> 集合返回单个设置。  
  
 与类别和子类别一样，每个设置具有一个是唯一字符串的标识符。 例如，`TextEditor.Basic` 页上的“制表符大小”设置由字符串 `TabSize` 标识。  
  
> [!NOTE]
>  由于本地化和其他原因，在“选项”页上显示的名称可能与用作设置标识符的字符串不同。 如果标识符未记录在其他位置，你可能必须使用自动化来查询 IDE 以获得正确的标识符。  
  
 你可以使用由 <xref:EnvDTE.Properties> 集合的 <xref:EnvDTE.Properties.Item%2A> 方法返回的 <xref:EnvDTE.Property> 对象的 <xref:EnvDTE.Property.Value%2A> 来查询并更改设置状态。  
  
 例如，若要通过自动化模型设置 `TextEditor.Basic` 页面上的“制表符大小”设置，使用以下示例中返回的 <xref:EnvDTE.Properties> 对象。  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 下面的示例演示如何使用 MPF 更新“制表符大小”设置。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 有关详细信息，请参阅[控制选项设置](../Topic/Controlling%20Options%20Settings.md)。  
  
## 保持选项页设置  
 IDE 实现完全支持 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动化模型的“选项”页的状态持久性。  
  
 当用户点击“工具”菜单上的“导入\/导出设置”命令时，包括在 IDE 中的页上的设置会自动进行保存（或检索）。  
  
 你可以通过将 `ProfileSave` 标识添加到 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS Version\>*\\AutomationProperties（其中 *\<VS Version\>* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本的版本号）下的自定义“选项”页注册表项，启用自定义“选项”页，以使用该自动持久性支持。 有关更多信息，请参见[注册自定义选项页](../misc/registering-custom-options-pages.md)。  
  
## 请参阅  
 [使用互操作程序集创建选项页](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [创建选项页](../extensibility/internals/creating-options-pages.md)   
 [使用自动化创建选项页](../misc/creating-options-pages-by-using-automation.md)   
 [控制选项设置](../Topic/Controlling%20Options%20Settings.md)   
 [注册自定义选项页](../misc/registering-custom-options-pages.md)   
 [打开选项页](../misc/opening-an-options-page.md)   
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)