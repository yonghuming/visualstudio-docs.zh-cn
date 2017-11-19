---
title: "在关系图上设置背景图像 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 13e52e30ebeda4d881474bcf990068d1a92bb7f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setting-a-background-image-on-a-diagram"></a>在图表上设置背景图像
在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可视化和建模 SDK 中，可以使用自定义代码为生成的设计器设置背景图像。  
  
## <a name="setting-the-background-image"></a>设置背景图像  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>为生成的设计器设置背景图像  
  
1.  将要用作关系图的背景的图像文件复制到当前项目的 Dsl\Resources 目录中。  
  
2.  在**解决方案资源管理器**，右键单击 Dsl\Resources 文件夹，指向**添加**，然后单击**现有项**。  
  
3.  在**添加现有项**对话框中，浏览到 Dsl\Resources 文件夹。  
  
4.  在**类型的文件**列表中，单击**映像文件**。  
  
5.  单击复制到目录，该图像文件，然后单击**添加**。  
  
6.  右键单击 Dsl，然后单击**属性**以打开 Dsl 项目的属性。  
  
7.  上**资源**选项卡上，单击**此项目不包含默认资源文件。单击此处创建一个资源文件。”**。  
  
8.  将图像文件添加到资源文件，通过拖动从图片**解决方案资源管理器**到资源窗口。  
  
9. 打开“文件”菜单，然后单击该选项以保存项目属性。  
  
10. 验证文件 Dsl\Properties\Resources.resx 是否存在，以及该文件下面是否具有文件 Resources.Designer.cs。  
  
11. 如果缺少 Resources.Designer.cs 时，请单击文件 Resources.resx 中**解决方案资源管理器**。  
  
12. 在**属性**窗口中，设置`Custom Tool`属性`ResXFileCodeGenerator`。  
  
13. 在**解决方案资源管理器**，右键单击 Dsl 项目，指向**添加**，然后单击**新文件夹**。  
  
14. 将文件夹命名为**自定义**。  
  
15. 右键单击自定义文件夹，指向**添加**，然后单击**新项**。  
  
16. 在**添加新项**对话框中，在**模板**列表中，单击**代码文件**。  
  
17. 在**名称**框中，键入`BackgroundImage.cs`，然后单击**添加**。  
  
18. 将以下代码复制到 BackgroundImage.cs 文件，从而调整命名空间、关系图类名以及图像文件资源名称。  
  
     将“MyDiagramClass”替换为在 Dsl\GeneratedCode\Diagrams.cs 中定义的关系图分部类的名称。 还可以从文件 Dsl\GeneratedCode\Diagrams.cs 中检索正确的命名空间。  
  
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
  
     有关自定义与程序代码模型的详细信息，请参阅[导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## <a name="see-also"></a>另请参阅  
 [定义形状和连接符](../modeling/defining-shapes-and-connectors.md)   
 [自定义文本和图像字段](../modeling/customizing-text-and-image-fields.md)   
 [导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [编写代码以自定义域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
