---
title: "自定义和扩展的域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: "48"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: efdd7f5358ce0ec4afd32ebaa8ff1fd8d117dc47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>自定义和扩展域特定语言
Visual Studio 建模和可视化效果 SDK (VMSDK) 提供可以在其中定义建模工具的多个级别：  
  
1.  定义使用 DSL 定义关系图的域特定语言 (DSL)。 使用图表的表示法，可读的 XML 格式，并生成代码和其他项目所需的基本工具，可以快速创建 DSL。  
  
     有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  
  
2.  通过使用更高级的 DSL 定义功能来微调 DSL。 例如，你可创建用户创建的元素时显示的其他链接。 这些技术通常在 DSL 定义中，来实现，但有些需要的程序代码的几行。  
  
3.  通过使用程序代码来扩展你的建模工具。 VMSDK 专门用于轻松将扩展和从 DSL 定义生成的代码相集成。  有关详细信息，请参阅[编写代码，以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。  
  
> [!NOTE]
>  已更新 DSL 定义文件，不要忘记单击**转换所有模板**在重新生成你的解决方案之前的解决方案资源管理器工具栏中。  
  
##  <a name="customShapes"></a>本节内容  
  
|若要实现这种效果|请参阅本主题|  
|----------------------------|-------------------------|  
|允许用户设置形状的颜色和样式属性。|右击形状或连接器类，指向**添加公开**，并单击的项。<br /><br /> 请参阅[自定义关系图上的演示文稿](../modeling/customizing-presentation-on-the-diagram.md)。|  
|不同的模型元素的类关系图中，共享属性，例如初始高度和宽度、 颜色、 工具提示上类似。|使用形状或连接器类之间的继承。 派生的形状和派生的域类之间的映射继承父项的映射详细信息。<br /><br /> 或者，将不同的域类映射到同一个形状类。|  
|按不同的形状上下文显示模型元素的类。|将多个形状类映射到相同的域类。 生成解决方案时，遵循错误报告，并提供请求的代码，以决定要使用哪些形状。|  
|形状颜色或字体等其他功能则指示当前的状态。|请参阅[更新以反映模型的形状和连接符](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 创建更新公开的属性的规则。 请参阅[规则将在模型内的更改传播](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，使用 OnAssociatedPropertyChanged() 更新非公开的功能，例如链接箭头或字体。|  
|形状更改来指示状态的图标。|在 DSL 详细信息窗口中设置的可见性的修饰器映射。 找到的相同位置中的多个映像修饰器。 请参阅[更新以反映模型的形状和连接符](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或重写`ImageField.GetDisplayImage()`。 请参阅中的示例<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>。|  
|在任何形状上设置背景图像|重写 InitializeInstanceResources() 添加锚定的 ImageField。 请参阅[自定义关系图上的演示文稿](../modeling/customizing-presentation-on-the-diagram.md)。|  
|对于任何深度的嵌套形状|设置嵌入树递归。 定义 BoundsRules 以包含形状。 请参阅[自定义关系图上的演示文稿](../modeling/customizing-presentation-on-the-diagram.md)。|  
|附加在固定点元素的边界上的连接器。|定义嵌入终端的元素，由关系图上的小端口。 使用 BoundsRules 就地修复端口。 请参阅的线路关系图示例[可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)。|  
|文本字段显示值派生自其他值。|映射到计算或自定义存储域属性的文本修饰。 有关详细信息，请参阅[计算和自定义存储属性](../modeling/calculated-and-custom-storage-properties.md)。|  
|将模型元素之间的或形状之间的更改传播|请参阅[域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)。|  
|将更改传播到等其他资源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]store 外的扩展。|请参阅[事件处理程序将在模型外部更改传播](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|  
|属性窗口将显示一个相关的元素的属性。|设置属性转发。 请参阅[自定义属性窗口](../modeling/customizing-the-properties-window.md)。|  
|属性类别|属性窗口划分为称为类别的各部分中。 设置**类别**的域属性。 具有相同的类别名称的属性将显示在相同的部分。 你还可以设置**类别**关系角色。|  
|控制用户访问域属性|设置**是可浏览**false 以防止域属性在运行时显示在属性窗口中。 你仍可以将其映射到文本修饰器。<br /><br /> **是一个 UI 只读选项**防止用户更改域属性。<br /><br /> 不会影响程序的 domain 属性可以访问。|  
|更改名称、 图标和 DSL 的模型资源管理器中的节点的可见性。|请参阅[自定义模型资源管理器](../modeling/customizing-the-model-explorer.md)。|  
|启用复制、 剪切和粘贴|设置**启用复制粘贴**属性**编辑器**DSL 资源管理器中的节点。|  
|每当复制某个元素时，将复制引用链接和它们的目标。 例如，复制注释附加到的项。|设置**传播复制**（由 DSL 定义关系图的域关系的一端所在的行） 的源角色的属性。<br /><br /> 编写代码以覆盖 ProcessOnCopy 以实现更复杂的效果。<br /><br /> 请参阅[自定义复制行为](../modeling/customizing-copy-behavior.md)。|  
|删除、 重新设置父级，或删除元素时重新链接相关的元素。|设置**传播删除**关系角色的值。 对于更复杂的效果，重写`ShouldVisitRelationship`和`ShouldVisitRolePlayer`中的方法`MyDslDeleteClosure`中定义的类**DomainModel.cs**<br /><br /> 请参阅[自定义删除行为](../modeling/customizing-deletion-behavior.md)|  
|保留形状布局和外观上复制和拖放。|将形状和连接符添加到复制`ElementGroupPrototype`。 最方便的方法重写`ElementOperations.CreateElementGroupPrototype()`<br /><br /> 请参阅[自定义复制行为](../modeling/customizing-copy-behavior.md)。|  
|在所选位置（例如当前光标位置）粘贴形状。|重写`ClipboardCommandSet.ProcessOnCopy()`若要使用的位置特定版本`ElementOperations.Merge().`请参阅[自定义复制行为](../modeling/customizing-copy-behavior.md)。|  
|在粘贴上创建更多链接|重写 ClipboardCommandSet.ProcessOnPasteCommand()|  
|启用从拖放此关系图中，其他 Dsl 和 Windows 元素|请参阅[如何： 添加一个拖放处理程序](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|就像它已拖动到父上允许形状或工具拖动到子形状，如端口上。|一个元素合并指令对目标对象类定义，将转发到父级的拖放的对象。 请参阅[自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)。|  
|允许形状或工具拖动到一个形状上，并有其他链接或创建的对象。 例如，若要允许要将其拖到它是要链接的项中的注释。|对目标域类，定义一个元素合并指令并定义要生成的链接。 在复杂的情况下，你可以添加自定义代码。 请参阅[自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)。|  
|一种工具创建一的组元素。 例如，具有一组固定的端口的组件。|重写 ToolboxHelper.cs 中的工具箱初始化方法。 创建元素组原型 (EGP) 包含的元素以及它们关系的链接。 请参阅[自定义工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 请在 EGP，包括主体和端口形状或定义 BoundsRules EGP，实例化时放置端口形状。 请参阅[BoundsRules 约束形状位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)。|  
|使用一个连接工具来实例化几种类型的关系。|将链接连接指令 (LCD) 添加到由该工具调用连接生成器。 Lcd 确定两个元素的类型中的关系类型。 若要使这取决于元素的状态，你可以添加自定义代码。 请参阅[自定义工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|  
|粘性工具-用户可以双击用于连续创建许多形状或连接器的任何工具。|DSL 资源管理器，在选择`Editor`节点。 在属性窗口中，设置**使用粘性工具箱项**。|  
|定义菜单命令|请参阅[如何： 修改标准菜单命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|约束具有验证规则的模型|请参阅[域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)|  
|从 DSL 生成代码、 配置文件或文档。|[从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)|  
|自定义模型如何将保存到文件。|请参阅[自定义文件存储和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|将模型保存到数据库或其他媒体。|重写*YourLanguage*DocData<br /><br /> 请参阅[自定义文件存储和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|将多个 Dsl 集成，使它们作为一个应用程序的一部分工作。|请参阅[集成模型通过使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|  
|允许 DSL 由第三方扩展，并控制扩展。|[使用 MEF 扩展 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 库在 DSL 之间共享类](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定义锁定策略以创建只读段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>另请参阅  
 [如何定义的域特定语言](../modeling/how-to-define-a-domain-specific-language.md)   
 [编写代码以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Visual Studio 的建模 SDK - 特定于域的语言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

