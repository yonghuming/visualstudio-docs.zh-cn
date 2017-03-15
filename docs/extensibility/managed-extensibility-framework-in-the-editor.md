---
title: "Managed Extensibility Framework 编辑器中的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>在编辑器中的托管可扩展性框架
使用 Managed Extensibility Framework (MEF) 组件生成编辑器。 您可以生成您自己的 MEF 组件来扩展编辑器中，并且您的代码可以使用编辑器的组件。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>托管可扩展性框架概述  
 MEF 是一个.NET 库，您可以添加和修改应用程序或组件，它遵循 MEF 编程模型的功能。 Visual Studio 编辑器中可以同时提供和使用 MEF 部件的组件。  
  
 MEF 都包含在.NET Framework 版本 4 System.ComponentModel.Composition.dll 程序集。  
  
 有关 MEF 的详细信息，请参阅[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
### <a name="component-parts-and-composition-containers"></a>组件部件和撰写容器  
 组件部件是一个类或成员的可执行一个 （或两者） 的以下类︰  
  
-   使用另一个组件  
  
-   可供另一个组件  
  
 例如，考虑购物应用程序依赖于仓库库存组件提供的产品可用性数据订单项组件。 在 MEF 术语中，库存部件可以*导出*产品可用性数据，并且订单条目部件可以*导入*数据。 订单输入部分和库存部件不需要知道有关彼此;*撰写容器*（由宿主应用程序） 负责维护一组导出，并解决导出和导入。  
  
 撰写容器<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，通常拥有的主机。</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> 撰写容器维护*目录*的部件的导出的组件。  
  
### <a name="exporting-and-importing-component-parts"></a>导出和导入部件的组件  
 只要实现为公共类或类 （属性或方法） 的公共成员，您可以导出任何功能。 无需从<xref:System.ComponentModel.Composition.Primitives.ComposablePart>。</xref:System.ComponentModel.Composition.Primitives.ComposablePart>派生组件部件 相反，必须添加<xref:System.ComponentModel.Composition.ExportAttribute>属性设为类或你想要导出的类成员。</xref:System.ComponentModel.Composition.ExportAttribute> 此属性指定*协定*通过的另一个组件部件可以导入您的功能。  
  
### <a name="the-export-contract"></a>导出协定  
 <xref:System.ComponentModel.Composition.ExportAttribute>定义正在导出的实体 （类、 接口或结构）。</xref:System.ComponentModel.Composition.ExportAttribute> 通常情况下，export 特性采用一个参数以指定导出的类型。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 默认情况下，<xref:System.ComponentModel.Composition.ExportAttribute>属性定义的协定，这是导出类的类型</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 在示例中，默认值`[Export]`属性等同于`[Export(typeof(TestAdornmentLayerDefinition))]`。  
  
 此外可以导出的属性或方法，如下面的示例中所示。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>导入 MEF 导出  
 如果您想要使用 MEF 导出，您必须了解的协定 （一般类型） 时所依据它导出的并添加<xref:System.ComponentModel.Composition.ImportAttribute>属性的值。</xref:System.ComponentModel.Composition.ImportAttribute> 默认情况下，导入属性包含一个参数，这是它会修改类的类型。 以下几行代码导入<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>类型。</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>MEF 组件部件从获取编辑器的功能  
 如果您现有的代码是 MEF 组件部件，可以使用 MEF 元数据来使用编辑器部件的组件。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>若要使用的 MEF 组件部件的编辑器功能  
  
1.  将引用添加到 System.Composition.ComponentModel.dll，这是在全局程序集缓存 (GAC) 中，和编辑器程序集。  
  
2.  添加相关 using 语句。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  添加`[Import]`属性到您的服务接口，如下所示。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  当获取该服务后时，你可以使用任一及其组件。  
  
5.  当已编译您的程序集，将其放在...Visual Studio 安装 \Common7\IDE\Components\ 文件夹。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)
