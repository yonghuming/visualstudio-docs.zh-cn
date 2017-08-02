---
title: "在代码中创建依赖项关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: b17d12160920952170d042eb46191df66542c80a
ms.openlocfilehash: e51f32303496d20980d7442458cd35350db01687
ms.lasthandoff: 02/22/2017

---
# <a name="create-dependency-diagrams-from-your-code"></a>在代码中创建依赖项关系图
若要可视化软件系统的高级逻辑体系结构，创建*依赖项关系图*Visual Studio 中。 若要确保你的代码保持与此设计保持一致，请验证您的代码与依赖项关系图。 您可以创建 Visual C#.NET 和 Visual Basic.NET 项目的依赖项关系图。 若要查看哪些版本的 Visual Studio 支持此功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![创建一个依赖项关系图](~/docs/modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 依赖项关系图，你将 Visual Studio 解决方案项组织到名为的逻辑抽象组*层*。 你可以使用层来描述这些项目执行的主要任务或系统的主要组件。 每个层可包含描述更详细任务的其他层。 您还可以指定预期或现有*依赖关系*各层之间。 这些依赖项（表示为箭头）显示哪些层可以使用或当前正在使用由其他层表示的功能。 若要维护代码的体系结构控制，请在关系图上显示预期的依赖项，然后对照关系图验证代码。  
  
 [视频︰ 验证实时您体系结构的依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="a-namecreatediagrama-create-a-dependency-diagram"></a><a name="CreateDiagram"></a>创建一个依赖项关系图  
 创建依赖项关系图之前，请确保您的解决方案具有一个建模项目。 
  
> [!IMPORTANT]
>  不要添加、 拖动，或将从一个建模项目的现有依赖项关系图复制到另一个建模项目或解决方案中的另一个位置。 这将保留原始关系图中的引用，即使你更改此关系图。 这也将阻止层验证正常操作，并可能导致出现其他问题，例如，尝试打开该关系图时元素缺失或出现其他错误。  
>   
>  相反，将新的依赖项关系图添加到建模项目。 将源关系图中的元素复制到新关系图中。 保存建模项目和新的依赖项关系图。  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>若要向建模项目中添加一个新的依赖项关系图  
  
1.  在**体系结构**菜单上，选择**新的依赖项关系图**。  
  
2.  在下**模板**，选择**依赖项关系图**。  
  
3.  命名该关系图。  
  
4.  在**将添加到建模项目**，浏览到并在解决方案中选择一个现有建模项目。  
  
     - 或 -  
  
     选择**创建新的建模项目**将一个新建模项目添加到解决方案。  
  
    > [!NOTE]
    >  依赖项关系图必须存在于建模项目内。 但是，你可以将其链接到解决方案中任何位置的项。  
  
5.  请确保保存建模项目和依赖项关系图。  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>拖放，或复制并粘贴从代码图

1. 生成解决方案使用一个代码图**体系结构**菜单。 

2. 请考虑在应用代码图筛选要删除解决方案文件夹以及"测试资产"，如果你只想要强制在产品代码中的依赖项。

3. 在生成代码映射上，删除"External"节点，或其展开以显示外部程序集，具体取决于是否想要强制执行命名空间依赖项，并从代码映射中删除非必需程序集。 

4. 创建新的依赖项关系图的解决方案使用**体系结构**菜单

5. 选择代码图上的所有节点 (使用_Ctrl_ + _A_，或通过按使用橡皮筋选择_Shift_密钥之前单击、 拖动和释放。

6. 拖动和删除，或复制和粘贴，到新的依赖项验证关系图中所选元素。 

7. 这将显示当前应用程序体系结构。 决定你想要的体系结构并相应地修改依赖项关系图。

![从代码图生成依赖项关系图](~/docs/modeling/media/dependency-validation-01.png)
  
##  <a name="a-namecreatelayersa-create-layers-from-artifacts"></a><a name="CreateLayers"></a>从项目中创建层  
 你可以从 Visual Studio 解决方案项（如项目、代码文件、命名空间、类和方法）中创建层。 这将自动在这些层和项（包括在层验证过程中）之间创建链接。  
  
 你也可以将层链接到不支持验证的项（如 Word 文档或 PowerPoint 演示文稿）以便能够将层与规范或计划关联。 你还可以将层链接到项目中跨多个应用程序共享的文件，但验证过程将不包括带泛型名称（如“层 1”或“层 2”）的显示的层。  
  
 若要查看链接的项是否支持验证，请打开**层资源管理器**并检查**支持验证**该项目的属性。 请参阅[管理指向项目](#Managing)。  
  
|**若要**|**请按照下列步骤**|  
|------------|----------------------------|  
|为单个项目创建一个层|<ol><li>将项拖动到依赖项关系图从以下源︰<br /><br /> <ul><li>**解决方案资源管理器**<br /><br />         例如，您可以拖动文件或项目。</li><li>代码图<br /><br />         请参阅[映射解决方案之间的依赖关系](../modeling/map-dependencies-across-your-solutions.md)和[使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)。</li><li>**类视图**或**对象浏览器**</li></ul><br />     层显示在关系图上，并链接到项目。</li><li>重命名层以反映关联代码或项目的作用。</li></ol> **重要提示︰**将二进制文件拖动到依赖项关系图不会自动添加到建模项目及其引用。 你必须将要验证的二进制文件手动添加到建模项目中。 **将二进制文件添加到建模项目** <ol><li>在**解决方案资源管理器**，打开建模项目的快捷菜单，然后选择**添加现有项**。</li><li>在**添加现有项**对话框中，浏览到二进制文件，选中它们，，然后选择**确定**。     二进制文件将显示在建模项目中。</li><li>在**解决方案资源管理器**，选择的二进制文件已添加，然后按**F4**若要打开**属性**窗口。</li><li>在每个二进制文件上设置**生成操作**属性设置为**验证**。</li></ol>|  
|为所有选择的项目创建单个层|将所有项目同时都拖到依赖项关系图。<br /><br /> 一个层将出现在关系图上，并链接到所有这些项目。|  
|为每个所选的项目创建一个层|按下并保持**SHIFT**键的同时拖动的所有项目到依赖项关系图在同一时间。 **注意︰**如果您使用**SHIFT**键选择的项的范围，在选择了项目之后松开该键。 将这些项目拖到关系图上时再次按住该键。 <br /><br /> 每个项目的层将出现在关系图上，并链接到该项目。|  
|向层中添加项目|将项目拖到层上。|  
|创建新的未链接的层|在**工具箱**，展开**依赖项关系图**部分，然后拖动**层**到依赖项关系图。<br /><br /> 若要添加多个层，请双击该工具。 当完成后，选择**指针**工具或按**ESC**键。<br /><br /> - 或 -<br /><br /> 打开依赖项关系图的快捷菜单中，选择**添加**，然后选择**层**。|  
|创建嵌套的层|将现有层拖到另一个层上。<br /><br /> - 或 -<br /><br /> 打开层的快捷菜单中，选择**添加**，然后选择**层**。|  
|创建包含两个或更多现有层的新层|选择层，打开所选内容的快捷菜单，然后选择**组**。|  
|更改层的颜色|设置其**颜色**属性设置为所需的颜色。|  
|指定与层关联的项目必须不属于指定的命名空间|键入命名空间中的层**禁止的命名空间**属性。 使用分号 (**;**) 来分隔命名空间。|  
|指定与层关联的项目不能依赖于指定的命名空间|键入命名空间中的层**Forbidden Namespace Dependencies**属性。 使用分号 (**;**) 来分隔命名空间。|  
|指定与层关联的项目必须属于某个指定的命名空间|键入命名空间中的层**Required Namespaces**属性。 使用分号 (**;**) 来分隔命名空间。|  
  
 层上的数字指示链接到该层的项目数。 但在读取此数字时，请记住以下事项：  
  
-   如果某个层链接到一个包含其他项目的项目，但该层未直接链接到其他项目，则该数字仅包括链接的项目。 但是，在层验证过程中其他项目包括在分析范围内。  
  
     例如，如果一个层链接到单个命名空间，则链接的项目数是 1，即使该命名空间包含类也是如此。 如果该层还链接到命名空间中的每个类，则该数字将包括链接的类。  
  
-   如果一个层包含链接到项目的其他层，则容器层也链接到这些项目，即使容器层上的数字不包括这些项目。  
  
##  <a name="a-namemanaginga-manage-links-between-layers-and-artifacts"></a><a name="Managing"></a>管理层和项目之间的链接  
  
1.  在依赖项关系图中，打开层的快捷菜单，然后选择**查看链接**。  
  
     **层资源管理器**显示所选层的项目链接。  
  
2.  使用以下任务管理这些链接：  
  
|**若要**|**在层资源管理器**|  
|------------|---------------------------|  
|删除层与项目之间的链接|打开项目链接的快捷菜单，然后选择**删除**。|  
|将链接从一个层移到另一个层|将项目链接拖到关系图上的一个现有层。<br /><br /> - 或 -<br /><br /> 1.打开项目链接的快捷菜单，然后选择**剪切**。<br />2.在依赖项关系图中，打开层的快捷菜单，然后选择**粘贴**。|  
|将链接从一个层复制到另一个层|1.打开项目链接的快捷菜单，然后选择**副本**。<br />2.在依赖项关系图中，打开层的快捷菜单，然后选择**粘贴**。|  
|基于现有项目链接创建一个新层|将项目链接拖到关系图上的空白区域。|  
|验证链接的项目支持对依赖项关系图的验证。|看一下**支持验证**项目链接的列。|  
  
##  <a name="a-namediscoveringa-reverse-engineer-existing-dependencies"></a><a name="Discovering"></a>现有依赖关系进行反向工程处理  
 只要与一个层关联的项目引用与另一个层关联的项目，就存在依赖关系。 例如，一个层中的某个类声明了一个拥有其他层中的某个类的变量。 您可以对关系图上链接到层的项目的现有依赖关系进行反向工程处理。  
  
> [!NOTE]
>  无法为某些种类的项目对依赖关系进行反向工程处理。 例如，对于链接到文本文件的层，将不会对源自或指向该层的依赖关系进行反向工程处理。 若要查看哪些项目具有可进行反向工程处理依赖项，打开一个或多个层的快捷菜单，然后选择**查看链接**。 在**层资源管理器**，检查**支持验证**列。 依赖项不会为其此列显示的项目实施反向工程**False**。  
  
-   选择一个或多个层，打开所选的层的快捷菜单，然后选择**生成依赖项**。  
  
 通常，您会看到一些不应存在的依赖关系。 可以编辑这些依赖关系，使它们与预期的设计对齐。  
  
##  <a name="a-nameeditdependenciesa-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a>编辑层和依赖项以显示预期的设计  
 若要描述你计划对您的系统或计划的体系结构进行的更改，请编辑依赖项关系图︰  
  
|**若要**|**执行这些步骤**|  
|------------|-----------------------------|  
|更改或限制依赖项的方向|设置其**方向**属性。|  
|创建新的依赖项|使用**依赖项**和**双向依赖项**工具。<br /><br /> 若要绘制多个依赖关系，请双击该工具。 当完成后，选择**指针**工具或按**ESC**键。|  
|指定与层关联的项目不能依赖于指定的命名空间|键入命名空间中的层**Forbidden Namespace Dependencies**属性。 使用分号 (**;**) 来分隔命名空间。|  
|指定与层关联的项目必须不属于指定的命名空间|键入命名空间中的层**禁止的命名空间**属性。 使用分号 (**;**) 来分隔命名空间。|  
|指定与层关联的项目必须属于某个指定的命名空间|键入命名空间中的层**Required Namespaces**属性。 使用分号 (**;**) 来分隔命名空间。|  
  
##  <a name="a-nameeditlayouta-change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a>更改元素在关系图的显示方式  
 通过编辑层或依赖项的属性，你可以更改层的大小、形状、颜色和位置或依赖项的颜色。  
  
##  <a name="a-namecodemapsa-discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a>发现的模式和在代码图上的依赖关系  
 在创建依赖项关系图时，您可以创建**代码图**。 这些关系图可以帮助你在浏览代码时发现模式和依赖项。 使用解决方案资源管理器、类视图或对象浏览器来浏览程序集、命名空间和类，这通常能很好地响应现有层。 有关代码图的详细信息，请参阅：  
  
-   [映射解决方案中的依赖项](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [使用代码图分析查找潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>另请参阅  
 [视频︰ 验证实时您体系结构的依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)   
 [依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)   
 [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)   
 [代码可视化](../modeling/visualize-code.md)

