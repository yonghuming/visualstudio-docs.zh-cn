---
title: "本地化 SharePoint 解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8186110b04e3ff56b3c6b0cad03890f3233c03d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-sharepoint-solutions"></a>本地化 SharePoint 解决方案
  准备你的应用程序，以便它们可以全球范围内使用的过程被称为本地化。 本地化所转换到特定区域性的资源。 有关详细信息，请参阅[Globalizing 和本地化应用程序](/visualstudio/ide/globalizing-and-localizing-applications)。 本主题提供有关如何本地化 SharePoint 解决方案的概述。  
  
 若要本地化解决方案时，请从代码中删除的硬编码字符串，且它们提取到资源文件。 资源文件是[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-基于带.resx 扩展名的文件。 资源文件包含你的解决方案中使用的字符串翻译的版本。 有关详细信息，请参阅[应用程序中的资源](http://go.microsoft.com/fwlink/?LinkID=155844)。  
  
> [!NOTE]  
>  将只有字符串资源添加到 SharePoint 解决方案的资源文件。 资源编辑器使你能够添加非字符串资源，尽管非字符串资源不会部署到 SharePoint。  
  
## <a name="resource-files"></a>资源文件  
 有三种类型的资源文件： 默认、 非特定语言和特定于语言的。  
  
|资源文件类型|描述|  
|------------------------|-----------------|  
|默认|也称为回退资源，默认资源文件包含针对默认区域性，如英语本地化的字符串。 如果找不到指定的语言不本地化的资源文件，使用它们。 默认资源没有单独的文件，它们存储在主应用程序程序集。|  
|非特定于语言的|资源文件，其中包含针对一种语言，但不是特定区域性本地化的字符串。 例如，"fr"为法语。|  
|特定于语言的|资源文件，其中包含一种语言和区域性本地化的字符串。 例如，"fr 的 CA"加拿大法语。|  
  
 有关详细信息，请参阅[分层组织的本地化资源用于](http://go.microsoft.com/fwlink/?LinkId=178360)。  
  
 若要在开发中的 SharePoint 项目中指定默认资源文件[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，选择**固定语言 （固定国家/地区）**中的区域性列表**添加资源**对话框时你将一个资源文件。  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>本地化 Visual Studio SharePoint 解决方案  
 在本地化解决方案时，应考虑的所有文本向用户显示你的解决方案的信息。 信息性消息、 错误消息和[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]字符串必须被转换，并且这些翻译放在资源文件。  
  
 在资源文件中的每个字符串都有唯一的标识符。 为每个资源文件中的已翻译字符串使用相同的标识符。 例如，如果"String1"是默认资源文件中的第一个字符串的标识符，则可以为特定于语言的资源文件中的第一个字符串使用相同的标识符。  
  
 有三个方面通常本地化中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 应用程序： 功能、 ASPX 页标记和代码。 为演示目的，以下部分假定你具有你想要将本地化为德语和日语的 SharePoint 解决方案。 默认语言为英语。  
  
### <a name="localizing-features"></a>本地化功能  
 若要本地化功能，你必须使用表达式引用的已翻译的标题和本地化的资源文件中的字符串替换硬编码的标题和说明的功能。 进行此更改中的**功能设计器**中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 有关详细信息，请参阅[如何： 本地化功能](../sharepoint/how-to-localize-a-feature.md)。  
  
 若要将英语功能本地化为德语和日语，应将三个资源文件项目项添加到你的项目： 分别用于英语、 德语和日语。 功能资源文件不能用于本地化 ASPX 标记或代码;将需要为其单独的资源文件。  
  
 创建功能资源文件后，向其中添加已翻译的字符串。 访问使用以下格式的表达式的本地化的字符串：  
  
```  
$Resources:String ID  
```  
  
 功能中的资源[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]始终被命名为资源。 如果你选择语言不同固定语言，然后区域性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]添加到资源文件名称。 例如，如果你添加的固定语言 （默认值） 功能资源文件，它称为 Resources.resx。 如果通过选择日语 （日本） 区域性中添加特定于语言的功能资源，文件被称为 Resources.ja JP.resx。 功能资源文件的名称会自动分配，并且无法更改。  
  
 范围的功能资源是本地与将它们添加到功能。 若要创建可由解决方案中的任何功能或元素文件的资源时，将添加**全局资源文件**而不是一个功能资源文件的项目项。 **全局资源文件**项目项位于**2010年**下的文件夹**SharePoint**中**添加新项**对话框。 全局资源文件将部署到 SharePoint 根文件夹的 \Resources 文件夹中。  
  
### <a name="localizing-aspx-page-markup"></a>本地化 ASPX 页标记  
 若要本地化[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]页，将三个资源文件项目项添加到你的项目： 分别用于英语、 德语和日语。 如果不需要本地化除标记之外的代码，你可以改为添加全局资源文件。  
  
 提供的默认语言资源文件的名称。 为相同的名称指定附加有特定于语言的区域性的本地化的资源文件[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 例如，对于德语的 MyAppResources.de DE.resx 和日语的 MyAppResources.ja JP.resx。  
  
 设置**部署类型**到每个资源文件的属性**AppGlobalResource**。 这将导致要部署到的 App_GlobalResources 文件夹，其中它们可供所有 ASPX 页和解决方案中的控件的资源文件。 App_GlobalResources 文件夹位于 C:\inetpub\wwwroot\wss\VirtualDirectories\\< 端口号\>\App_GlobalResources。  
  
> [!NOTE]  
>  如果你使用非全局资源文件，请将它们移到要启用的部署类型属性和其他特定于 SharePoint 的属性的项目项文件夹。  
  
 此外可以使用 ASPX 标记资源文件来本地化的代码。 如果你使用的资源来本地化除 ASPX 标记之外的代码，生成操作属性将设置保留的每个文件作为嵌入资源会导致资源要编译到附属程序集。 但是，如果将资源文件来本地化标记，你可以选择更改生成操作以防止其编译为主应用程序程序集文件的内容。  
  
 使用以下格式表达式替换 ASPX 页面和控件标记中的所有硬编码属性字符串：  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 对于文本形式的 ASPX，使用采用以下格式的表达式:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如:   
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 有关详细信息，请参阅[如何： 本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)。  
  
### <a name="localizing-code"></a>本地化代码  
 除了本地化功能字符串和[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]标记中，你还需要本地化的消息字符串和解决方案代码中显示的错误字符串。 本地化的信息性和错误消息包含在附属程序集。 附属程序集包含用户均可见，如字符串[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]文本和输出消息，如异常。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用标准.NET Framework 集散模型。 在中心或主程序程序集，包含的默认语言资源。 轮辐或附属程序集，包含特定于语言的资源。 有关详细信息，请参阅[打包和部署资源](http://go.microsoft.com/fwlink/?LinkId=179280)。 从资源 (.resx) 文件编译的附属程序集。 当将特定于语言的资源文件添加到你的项目和解决方案包中，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将资源文件编译到附属程序集中名为*项目名称*。 resources.dll。  
  
 与 ASPX 标记，通过将单独的资源文件项目项添加到你的项目; 本地化 SharePoint 应用程序代码一个用于默认语言，另一个用于每个本地化语言。 但是，如前所述，如果你已有用于本地化 ASPX 标记的资源文件，你可以重复使用它们来本地化代码。 如果你需要创建资源文件，请为默认语言资源文件提供一个带.resx 扩展名追加你选择的名称。 名称在相同的名称后追加的特定于语言的区域性的本地化的资源文件[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。 设置为嵌入的资源，若要启用的附属资源程序集创建的每个资源文件的生成操作属性。  
  
 若要创建的附属程序集，生成项目，然后将文件添加为其他程序集通过**高级**选项卡**包设计器**。 在添加程序集时，前面添加区域性[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]文件夹的位置路径，例如 DE-DE\\*项目项名称*。 resources.dll。 这使包内包含具有相同名称的文件。  
  
 在代码中，将硬编码字符串替换为对调用<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>方法使用以下语法：  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 有关详细信息，请参阅[如何： 本地化代码](../sharepoint/how-to-localize-code.md)。  
  
#### <a name="web-part-code-localization"></a>Web 部件代码本地化  
 Web 部件包括一种自定义属性编辑器功能，包括使用硬编码的字符串，如 WebDisplayName、 类别和 WebDescription 代码属性。 若要替换这些属性的字符串值，请创建单独的类派生自该特性的类。 在这些类中，设置属性的属性。 特性属性依赖于的基类。 例如，WebDisplayName 特性属性为 DisplayNameValue，WebDescription 属性属性为 DescriptionValue。  
  
 在派生类中，从资源文件以及要获取的本地化的值的字符串 id。 ResourceManager 对象引用的字符串 ID 此值返回到的属性编辑器特性。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何： 本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何： 本地化代码](../sharepoint/how-to-localize-code.md)   
 [如何： 将一个资源文件](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  