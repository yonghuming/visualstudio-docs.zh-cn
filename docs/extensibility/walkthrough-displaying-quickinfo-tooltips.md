---
title: "演练︰ 显示快速信息工具提示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>演练︰ 显示快速信息工具提示
快速信息 IntelliSense 功能，用于显示方法签名并说明当用户将指针移到方法名称。 您可以通过定义的标识符来提供快速信息的说明，然后创建工具提示中显示的内容来实现基于语言的功能，例如快速信息。 您可以定义快速信息的语言服务上下文中或可以定义你自己的文件名称扩展和内容类型，并且显示快速信息只是该类型的或现有的内容类型 （如"text") 中可显示快速信息。 本演练演示如何显示快速信息的"text"内容类型。  
  
 当用户将鼠标指针悬停在方法名，在本演练中的快速信息示例将显示工具提示。 这种设计要求您实现这些四个接口︰  
  
-   源接口  
  
-   源提供程序接口  
  
-   控制器接口  
  
-   控制器提供程序接口  
  
 源和控制器提供部件的 Managed Extensibility Framework (MEF) 组件，并负责将导出的源和控制器类和导入服务，如代理<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，后者可创建工具提示文本缓冲区中，与<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>，这样触发快速信息会话。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 在此示例中，快速信息源，使用硬编码列表方法名称和描述，但在完整的实现，该语言服务和相应语言文档是负责提供该内容。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
#### <a name="to-create-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`QuickInfoTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="implementing-the-quickinfo-source"></a>实现快速信息源  
 快速信息源是负责收集组的标识符和它们的说明，并将内容添加到工具提示文本缓冲区，当遇到的一个标识符时。 在此示例中，标识符和它们的说明是刚添加的源构造函数中。  
  
#### <a name="to-implement-the-quickinfo-source"></a>若要实现的快速信息源  
  
1.  添加一个类文件并将其命名`TestQuickInfoSource`。  
  
2.  添加对 Microsoft.VisualStudio.Language.IntelliSense 的引用。  
  
3.  添加以下导入。  
  
     [!code-vb[VSSDKQuickInfoTest&#1;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  声明的类，实现<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>，并将其命名`TestQuickInfoSource`。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  快速信息源提供程序、 文本缓冲区中，和方法名称和方法签名的一组中添加字段。 在此示例中，方法名称和签名进行初始化`TestQuickInfoSource`构造函数。  
  
     [!code-vb[VSSDKQuickInfoTest&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  添加一个构造函数设置的快速信息源提供程序和文本缓冲区，并填充的一套方法名称和方法签名和描述。  
  
     [!code-vb[VSSDKQuickInfoTest&#4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>方法。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 在此示例中，此方法找到当前的单词或上一如果游标是使用一条线或文本缓冲区的末尾。 如果该单词是一个方法名称，该方法名称的说明添加到快速信息内容。  
  
     [!code-vb[VSSDKQuickInfoTest&#5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  您还必须实现 dispose （） 方法中，因为<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>实现<xref:System.IDisposable>::</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&#6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>实现快速信息源提供程序  
 快速信息源的提供者提供主要是为了将自身作为 MEF 组件部件导出并实例化的快速信息源。 因为它是 MEF 组件部件，它可以导入其他 MEF 组件部件。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>若要实现快速信息源提供程序  
  
1.  声明名为快速信息源提供程序`TestQuickInfoSourceProvider`实现<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"工具提示快速信息源"<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的之前 ="default"，和一个<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"text"。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  导入两个编辑器服务，<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>和<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，为属性的`TestQuickInfoSourceProvider`。</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>返回一个新`TestQuickInfoSource`。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>实现快速信息控制器  
 快速信息控制器确定何时应显示快速信息。 在此示例中，当指针在值对应于一个方法名称的一个单词上时显示快速信息。 快速信息控制器实现的鼠标悬停事件处理程序触发快速信息会话。  
  
#### <a name="to-implement-a-quickinfo-controller"></a>若要实现的快速信息控制器  
  
1.  声明的类，实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>，并将其命名`TestQuickInfoController`。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  添加私有字段的文本视图中，在文本视图、 快速信息会话和快速信息控制器提供程序中表示的文本缓冲区。  
  
     [!code-vb[VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  添加一个构造函数，设置字段并将鼠标悬停事件处理程序。  
  
     [!code-vb[VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  添加的鼠标悬停事件处理程序触发快速信息会话。  
  
     [!code-vb[VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>方法，以便它将删除鼠标悬停事件处理程序，当从文本视图分离控制器。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>方法和<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>为此示例中的空方法的方法。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>实现快速信息控制器提供程序  
 快速信息控制器的提供者提供主要是为了将自身作为 MEF 组件部件导出并实例化的快速信息控制器。 因为它是 MEF 组件部件，它可以导入其他 MEF 组件部件。  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>若要实现快速信息控制器提供程序  
  
1.  声明一个名为类`TestQuickInfoControllerProvider`实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"工具提示快速信息控制器"和一个<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"text":</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  导入<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>作为属性。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[VSSDKQuickInfoTest&#17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>通过实例化的快速信息控制器的方法。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 QuickInfoTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>若要生成并测试 QuickInfoTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件并键入一些文本，其中包括单词"添加"和"减"。  
  
4.  将指针移到的匹配项的"添加"之一。 签名和说明`add`应显示方法。  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
