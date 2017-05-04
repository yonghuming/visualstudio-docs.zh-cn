---
title: "本地化 SharePoint 解决方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "全球化 [Visual Studio 中的 SharePoint 开发]"
  - "本地化 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发，本地化"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 本地化 SharePoint 解决方案
  准备应用程序以使其能够在全球范围内使用的过程称为本地化。  本地化是将资源翻译为特定的区域性。  有关更多信息，请参见[对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)。  本主题概述如何本地化 SharePoint 解决方案。  
  
 若要本地化解决方案，您将从代码中移除硬编码的字符串，并将它们提取到资源文件中。  资源文件是一种基于 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 的文件，扩展名为 .resx。  资源文件包含解决方案中使用的字符串的翻译版本。  有关更多信息，请参见 [Resources in Applications](http://go.microsoft.com/fwlink/?LinkID=155844)（应用程序中的资源）。  
  
> [!NOTE]  
>  仅向 SharePoint 解决方案资源文件中添加字符串资源。  尽管利用资源编辑器可以添加非字符串资源，但非字符串资源不会部署到 SharePoint。  
  
## 资源文件  
 共有三种资源文件：默认资源文件、非特定语言的资源文件以及特定语言的资源文件。  
  
|资源文件类型|描述|  
|------------|--------|  
|默认|也称为回退资源，默认资源文件包含针对默认区域性（例如英语）本地化的字符串。  如果找不到指定语言的本地化资源文件，则会使用它们。  默认资源没有单独的文件，它们存储在主应用程序程序集中。|  
|非特定语言|一种资源文件，其中包含针对某种语言（但不是特定区域性）本地化的字符串。  例如，“fr”表示法语。|  
|特定语言|一种资源文件，其中包含针对某种语言和区域性本地化的字符串。  例如，“fr\-CA”表示加拿大法语。|  
  
 有关详细信息，请参见 [Hierarchical Organization of Resources for Localization](http://go.microsoft.com/fwlink/?LinkId=178360)（用于本地化的资源的分层组织）。  
  
 若要在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中开发的 SharePoint 项目中指定默认资源文件，请在添加资源文件时，在“添加资源”对话框的区域性列表中选择“固定语言\(固定国家\/地区\)”。  
  
## 本地化 Visual Studio SharePoint 解决方案  
 在本地化解决方案时，您应考虑解决方案向用户显示的所有文本信息。  必须翻译信息性消息、错误消息和 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 字符串，并将这些翻译放在资源文件中。  
  
 资源文件中的每个字符串都有唯一的标识符。  请为每个资源文件中的翻译字符串使用同一标识符。  例如，如果“String1”是默认资源文件中第一个字符串的标识符，请为特定语言的资源文件中的第一个字符串使用同一标识符。  
  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 应用程序中，您通常本地化以下三个区域：功能、ASPX 页面标记和代码。  为便于阐释，以下各节假定您有一个要本地化为德语和日语的 SharePoint 解决方案。  默认语言为英语。  
  
### 本地化功能  
 若要本地化功能，您必须将功能硬编码的标题和说明替换为一个表达式，该表达式引用本地化的资源文件中的已翻译标题和字符串。  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的**“功能设计器”**中进行此更改。  有关更多信息，请参见[如何：本地化功能](../sharepoint/how-to-localize-a-feature.md)。  
  
 为了将英语功能本地化为德语和日语，您将向项目中添加三个资源文件项目项：分别用于英语、德语和日语。  无法使用功能资源文件来本地化 ASPX 标记或代码；这两者需要单独的资源文件。  
  
 创建功能资源文件后，请向其中添加翻译的字符串。  使用以下格式的表达式访问本地化的字符串：  
  
```  
$Resources:String ID  
```  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的功能资源始终命名为 Resources。  如果选择一种语言而非固定语言，则区域性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 将添加到资源文件名。  例如，如果添加固定语言（默认值）功能资源文件，则该文件称为“Resources.resx”。  如果通过选择日语的区域性（日本）来添加特定语言的功能资源，则文件名为 Resources.ja\-JP.resx。  功能资源文件名是自动指派的，无法进行更改。  
  
 功能资源的范围仅限于向其中添加这些资源的功能。  若要创建可由解决方案中的任何功能或元素文件使用的资源，请添加**“全局资源文件”**项目项，而不是功能资源文件。  **“全局资源文件”**项目项位于**“添加新项”**对话框的**“SharePoint”**下的**“2010”**文件夹中。  全局资源文件部署到 SharePoint 根文件夹的 \\Resources 文件夹。  
  
### 本地化 ASPX 页面标记  
 若要本地化 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 页，您需要将以下三个资源文件项目项添加到您的项目中：一个对应英语、一个对应德语，还有一个对应日语。  如果除了标记以外，您无须本地化代码，则可以取而代之添加全局资源文件。  
  
 为默认语言资源文件提供一个名称。  为本地化的资源文件指定附加有特定语言的区域性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 的相同名称。  例如，用于德语的 MyAppResources.de\-DE.resx 和用于日语的 MyAppResources.ja\-JP.resx。  
  
 将每个资源文件的**“部署类型”**属性设置为**“AppGlobalResource”**。  这样会使资源文件部署到 App\_GlobalResources 文件夹，在该文件夹中，这些资源文件可用于解决方案中的所有 ASPX 页面和控件。  App\_GlobalResources 文件夹位于 C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<端口号\>\\App\_GlobalResources 中。  
  
> [!NOTE]  
>  如果使用非全局资源文件，请将这些文件移到项目项文件夹中，以启用“部署类型”属性和其他特定于 SharePoint 的属性。  
  
 ASPX 标记资源文件也可用于本地化代码。  如果要使用资源来本地化除 ASPX 标记外的代码，请将每个文件的“生成操作”属性设置保留为“嵌入的资源”，以便将资源编译为附属程序集。  不过，如果您仅使用资源文件来本地化标记，则可以选择将“生成操作”更改为“内容”以防止将文件编译为主应用程序程序集。  
  
 将 ASPX 页面和控件标记中的所有硬编码属性字符串替换为以下格式的表达式：  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 对于文本形式的 ASPX，请使用以下格式的表达式：  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 有关详细信息，请参阅 [如何：本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)。  
  
### 本地化代码  
 除了本地化功能字符串和 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 标记外，您还必须本地化解决方案代码中出现的消息字符串和错误字符串。  本地化信息和错误消息包含在附属程序集中。  附属程序集包含用户可见的字符串，例如 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文本和异常等输出消息。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用标准 .NET Framework 集散模型。  集线器（或主程序程序集）包含默认语言资源。  轮辐（或附属程序集）包含特定语言的资源。  有关更多信息，请参见 [Packaging and Deploying Resources](http://go.microsoft.com/fwlink/?LinkId=179280)（打包和部署资源）。  附属程序集是从资源 \(.resx\) 文件编译的。  当您将特定语言的资源文件添加到项目和解决方案包时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将资源文件编译为名为“*Project Name*.resources.dll”的附属程序集。  
  
 与 ASPX 标记一样，通过向项目中添加单独的资源文件项目项来本地化 SharePoint 应用程序代码；一个表示默认语言，另一个表示每种本地化的语言。  不过，如上所述，如果您已经有用于本地化 ASPX 标记的资源文件，则可以重用它们来本地化代码。  如果需要创建资源文件，请为默认语言资源文件指定附加有 .resx 扩展名的所选名称。  为本地化的资源文件指定附加有特定语言的区域性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 的相同名称。  将每个资源文件的“生成操作”属性设置为“嵌入的资源”，以便能够创建附属资源程序集。  
  
 若要创建附属程序集，请生成项目，然后通过**“包设计器”**的**“高级”**选项卡添加文件作为附加程序集。  在添加程序集时，请在位置路径前面添加区域性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 文件夹，例如 de\-DE\\*Project Item Name*.resources.dll。  这样将允许包包含具有相同名称的文件。  
  
 在代码中，使用以下语法将硬编码的字符串替换为对 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法的调用：  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 有关详细信息，请参阅 [如何：本地化代码](../sharepoint/how-to-localize-code.md)。  
  
#### Web 部件代码本地化  
 Web 部件包括自定义属性编辑器功能，其中包括使用硬编码字符串的代码特性，例如 WebDisplayName、Category 和 WebDescription。  若要替换这些特性的字符串值，请创建一个派生自特性的类的单独的类。  在这些类中，设置特性的属性。  特性属性依赖于基类。  例如，WebDisplayName 特性属性为 DisplayNameValue，WebDescription 特性属性为 DescriptionValue。  
  
 在派生的类中，引用资源文件和 ResourceManager 对象中的字符串 ID 以获取该字符串 ID 的本地化值。  将此值返回到属性编辑器特性。  
  
## 请参阅  
 [如何：本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：本地化代码](../sharepoint/how-to-localize-code.md)   
 [如何：添加资源文件](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  