---
title: "如何： 扩展的域特定语言设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: "9"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 44b3ea3d3997ac781b02220316810f00826f2beb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>如何：扩展域特定语言设计器
你可以扩展的设计器，用于编辑 DSL 定义。 你可以添加更多菜单命令添加处理程序拖双击手势和特定类型的值或关系更改时触发的规则的扩展的类型。 扩展可打包为 Visual Studio 集成扩展 (VSIX)，并可以分发给其他用户。  
  
 有关示例代码以及有关此功能的详细信息，请参阅 Visual Studio[可视化和建模 SDK (VMSDK) 网站](http://go.microsoft.com/fwlink/?LinkID=186128)。  
  
## <a name="setting-up-the-solution"></a>设置该解决方案  
 设置一个包含你的扩展的代码项目和一个导出该项目的 VSIX 项目。 你的解决方案可以包含其他并入同一个 VSIX 的项目。  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>若要创建 DSL 设计器扩展解决方案  
  
1.  创建新项目使用的类库项目模板。 在**新项目**对话框中，单击**Visual C#** ，然后在中间的窗口中单击**类库**。  
  
     此项目将包含你的扩展的代码。  
  
2.  创建新项目使用 VSIX 项目模板。 在**新项目**对话框框中，展开**Visual C#**，单击**扩展性**，然后在中间的窗口中选择**VSIX 项目**。  
  
     选择**将添加到解决方案**。  
  
     在 VSIX 清单编辑器中打开 Source.extension.vsixmanifest。  
  
3.  以上内容的字段中，单击**添加内容**。  
  
4.  在**添加内容**对话框中，设置**选择内容类型**到**MEF 组件**，并设置**项目**到你的类库项目。  
  
5.  单击**选择版本**并确保**Visual Studio Enterprise**已选中。  
  
6.  请确保将 VSIX 项目的解决方案的启动项目。  
  
7.  在类库项目，添加对以下程序集的引用：  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## <a name="testing-and-deployment"></a>测试和部署  
 在本主题中测试任何扩展，生成和运行解决方案。 将打开 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的实验实例。 在此实例中，打开 DSL 解决方案。 编辑 DslDefinition 关系图。 扩展行为，可以查看。  
  
 若要将扩展部署到主[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，和其他计算机，请按照下列步骤：  
  
1.  查找 VSIX 安装文件，在 VSIX 项目中 bin\\*\\\*.vsix  
  
2.  将此文件复制到目标计算机，然后在 Windows 资源管理器 （或文件资源管理器） 中，双击它。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展管理器将打开，以确认是否已安装扩展。  
  
 若要卸载该扩展，请按照下列步骤：  
  
1.  在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]上**工具**菜单上，单击**扩展管理器**。  
  
2.  选择的扩展，并将其删除。  
  
## <a name="adding-a-shortcut-menu-command"></a>添加的快捷方式菜单命令  
 若要使 DSL 设计器图面上或在 DSL 资源管理器窗口中出现的快捷方式菜单命令，编写类似于以下的类。  
  
 类必须实现`ICommandExtension`并且必须具有该属性`DslDefinitionModelCommandExtension`。  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## <a name="handling-mouse-gestures"></a>处理鼠标手势  
 代码将类似于菜单命令的代码。  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## <a name="responding-to-value-changes"></a>响应值更改  
 此处理程序需要域模型正常工作。 我们提供了简单的域模型。  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 下面的代码实现一个简单的模型。 创建一个新的 GUID，将占位符。  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```