---
title: "托管在编辑器中的扩展性框架 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4677b10d54a6c591c2f60e4c0b1f2978ad49a0ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>在编辑器中的 managed 的 Extensibility Framework
使用 Managed Extensibility Framework (MEF) 组件生成的编辑器。 你可以构建自己的 MEF 组件来扩展编辑器和你的代码可以使用编辑器的组件。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed 的 Extensibility Framework 概述  
 MEF 是一个.NET 库，，可以添加和修改应用程序或遵循 MEF 编程模型的组件的功能。 Visual Studio 编辑器可以同时提供和使用 MEF 组件部分。  
  
 MEF 被包含在.NET Framework 版本 4 System.ComponentModel.Composition.dll 程序集。  
  
 有关 MEF 的详细信息，请参阅[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。  
  
### <a name="component-parts-and-composition-containers"></a>组件部件和撰写容器  
 组件部件是一个类或可执行一个 （或两者） 的以下类的成员：  
  
-   使用另一个组件  
  
-   可供其他组件  
  
 例如，考虑购物具有的应用程序依赖于产品可用性数据仓库清单组件提供的顺序条目组件。 在 MEF 术语中，清单部分还可以*导出*产品可用性数据，并且顺序条目部件可以*导入*数据。 顺序输入部分和清单部分不需要了解的有关每个其他;*撰写容器*（由主机应用程序） 负责维护的导出的一组和解决导出和导入。  
  
 撰写容器中， <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，通常拥有的主机。 撰写容器维护*目录*的导出的组成部分。  
  
### <a name="exporting-and-importing-component-parts"></a>导出和导入部件的组件  
 你可以导出任何功能，只要它作为公共类或类 （属性或方法） 的公共成员实现。 无需派生从你组件一部分<xref:System.ComponentModel.Composition.Primitives.ComposablePart>。 相反，你必须添加<xref:System.ComponentModel.Composition.ExportAttribute>属性设为类或你想要导出的类成员。 此属性指定*协定*通过的另一个组件部分可以导入你的功能。  
  
### <a name="the-export-contract"></a>导出协定  
 <xref:System.ComponentModel.Composition.ExportAttribute>定义正在导出的实体 （类、 接口或结构）。 通常情况下，导出属性采用一个参数，指定导出的类型。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 默认情况下，<xref:System.ComponentModel.Composition.ExportAttribute>属性定义的导出类的类型的协定。  
  
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
 如果你想要使用 MEF 导出，你必须知道的协定 （通常的类型） 依据它导出的并添加<xref:System.ComponentModel.Composition.ImportAttribute>具有该值的属性。 默认情况下，导入属性采用一个参数，这是它会修改类的类型。 下面的代码导入行<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>类型。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>获取从某一 MEF 组件部分的编辑器功能  
 如果现有代码是 MEF 组件部分，你可以使用 MEF 元数据来使用编辑器组件部分。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>若要使用某一 MEF 组件部分中的编辑器功能  
  
1.  将引用添加到 System.Composition.ComponentModel.dll，位于全局程序集缓存 (GAC) 中，以及编辑器程序集。  
  
2.  添加相关 using 语句。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  添加`[Import]`属性到你的服务接口，如下所示。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  当你已获得服务时，你可以使用任一及其组件。  
  
5.  当已编译您的程序集，将其放入...安装的 Visual Studio \Common7\IDE\Components\ 文件夹。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)