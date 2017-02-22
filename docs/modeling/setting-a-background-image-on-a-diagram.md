---
title: "在图表上设置背景图像 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 在图表上设置背景图像
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可视化和建模 SDK 中，可以使用自定义代码为生成的设计器设置背景图像。  
  
## 设置背景图像  
  
#### 为生成的设计器设置背景图像  
  
1.  将要用作关系图的背景的图像文件复制到当前项目的 Dsl\\Resources 目录中。  
  
2.  在**“解决方案资源管理器”**中，右键单击 Dsl\\Resources 文件夹、指向**“添加”**，然后单击**“现有项”**。  
  
3.  在**“添加现有项”**对话框中，浏览到 Dsl\\Resources 文件夹。  
  
4.  在**“文件类型”**框中，单击**“图像文件”**。  
  
5.  单击已复制到目录中的图像文件，然后单击**“添加”**。  
  
6.  右键单击 DSL，然后单击**“属性”**以打开 DSL 项目的属性。  
  
7.  在**“资源”**选项卡上，单击**“此项目不包含默认资源文件。单击此处创建一个资源文件。”**。  
  
8.  通过将图片从**“解决方案资源管理器”**拖动到资源窗口中，将图像文件添加到资源文件。  
  
9. 打开“文件”菜单，然后单击该选项以保存项目属性。  
  
10. 验证文件 Dsl\\Properties\\Resources.resx 是否存在，以及该文件下面是否具有文件 Resources.Designer.cs。  
  
11. 如果缺少 Resources.Designer.cs，则在**“解决方案资源管理器”**中单击文件 Resources.resx。  
  
12. 在**“属性”**窗口中，将 `Custom Tool` 属性设置为 `ResXFileCodeGenerator`。  
  
13. 在**“解决方案资源管理器”**中，右键单击 DSL 项目、指向**“添加”**，然后单击**“新建文件夹”**。  
  
14. 将该文件夹命名为“Custom”。  
  
15. 右键单击“Custom”文件夹、指向**“添加”**，然后单击**“新建项”**。  
  
16. 在**“添加新项”**对话框的**“模板”**列表中，单击**“代码文件”**。  
  
17. 在**“名称”**框中，键入 `BackgroundImage.cs`，然后单击**“添加”**。  
  
18. 将以下代码复制到 BackgroundImage.cs 文件，从而调整命名空间、关系图类名以及图像文件资源名称。  
  
     将“MyDiagramClass”替换为在 Dsl\\GeneratedCode\\Diagrams.cs 中定义的关系图分部类的名称。  还可以从文件 Dsl\\GeneratedCode\\Diagrams.cs 中检索正确的命名空间。  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     有关使用程序代码自定义模型的详细信息，请参阅[在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## 请参阅  
 [定义形状和连接线](../modeling/defining-shapes-and-connectors.md)   
 [自定义文本和图像字段](../modeling/customizing-text-and-image-fields.md)   
 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [编写代码以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)