---
title: "如何︰ 创建自定义文本标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的自定义文本标记"
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何︰ 创建自定义文本标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果你想要创建自定义文本标记，来强调或将代码组织，你必须执行以下步骤︰  
  
-   注册新的文本标记中，以便其他工具可以访问它  
  
-   提供的默认实现和配置的文本标记  
  
-   创建一个服务可以由其他进程使用以使文本标记的使用  
  
 有关如何将文本标记应用到代码区域的详细信息，请参阅 [如何︰ 使用文本标记](../extensibility/how-to-use-text-markers.md)。  
  
### <a name="to-register-a-custom-marker"></a>若要注册自定义标记  
  
1.  创建注册表项，如下所示︰  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< 版本>*\Text Editor\External 标记\\*\< MarkerGUID>*  
  
     *\< MarkerGUID>*是 `GUID` 用于标识要添加标记  
  
     *\< 版本>* 是版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，例如 8.0  
  
     *\< PackageGUID>* 是 VSPackage 实现自动化对象的 GUID。  
  
    > [!NOTE]
    >  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路径\\*\< 版本>* 初始化 Visual Studio shell 时，有关详细信息，请参阅可以替换备用根 [命令行开关](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
2.  创建四个值下 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< 版本>*\Text Editor\External 标记\\*\< MarkerGUID>*  
  
    -   (默认)  
  
    -   服务  
  
    -   DisplayName  
  
    -   package  
  
    -   `Default` 是可选为 REG_SZ 条目。 设置时，项的值是包含一些有用的标识信息，例如"自定义文本标记"的字符串。  
  
    -   `Service` 类型为 REG_SZ 项所在的服务，它提供的自定义文本标记 proffering 此 GUID 字符串 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>。 格式为 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
    -   `DisplayName` 类型为 REG_SZ 项所在的自定义文本标记的名称的资源 ID。 格式为 #YYYY。  
  
    -   `Package` 是项的类型 REG_SZ 包含 `GUID` VSPackage 提供服务的服务下列出。 格式为 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
### <a name="to-create-a-custom-text-marker"></a>若要创建自定义文本标记  
  
1.  实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 接口。  
  
     此接口的实现定义的行为和外观的自定义标记类型。  
  
     时，将调用此接口  
  
    1.  用户首次启动 IDE。  
  
    2.  用户选择 **重置默认** 按钮下 **字体和颜色** 属性页中的 **环境** 位于的左窗格中的文件夹 **选项** 对话框从获取 **工具** 在 IDE 的菜单。  
  
2.  实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> 方法，指定其 `IVsPackageDefinedTextMarkerType` 实现应返回基于上标记类型的方法调用中指定的 GUID。  
  
     则环境将调用此方法第一个时间你自定义标记的类型会创建，并指定一个标识的自定义标记类型的 GUID。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>若要作为服务 proffer 标记类型  
  
1.  调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>。  
  
     指向的指针 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 返回。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 方法，指定的 GUID 标识你自定义标记类型的服务并提供指向的实现的 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 接口。 你 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 实现应返回指针实现的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> 接口。  
  
     一个标识你的服务返回唯一的 cookie。 更高版本可以使用此 cookie 撤消你的自定义标记类型服务通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 接口指定此 cookie 值。  
  
## <a name="see-also"></a>请参阅  
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何︰ 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)   
 [如何︰ 实现错误标记](../extensibility/how-to-implement-error-markers.md)   
 [如何︰ 使用文本标记](../extensibility/how-to-use-text-markers.md)