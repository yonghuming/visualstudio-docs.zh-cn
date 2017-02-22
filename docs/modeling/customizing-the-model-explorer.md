---
title: "自定义模型资源管理器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "域特定语言工具, 域特定语言工具资源管理器"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 自定义模型资源管理器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以更改资源管理器的外观和行为域特定语言设计器于以下情况:  
  
-   更改窗口标题。  
  
-   更改选项 " 图标。  
  
-   更改节点的图标。  
  
-   隐藏节点。  
  
## 更改窗口标题  
 若要更改此位生成的 macro 资源管理器窗口标题，选择 " **资源管理器行为** 在 **DSL 资源管理器**，然后在 **属性** 窗口中，将 **前缀** 属性设置为所需的标题。  
  
## 更改选项 " 图标  
 若要更改此位资源管理器的选项 " 图标，请使用 " 16x16 像素的图标在 .bmp 文件。  将图标文件。 \\DslPackage\\Resources\\ folder， and then change the file name to ModelExplorerToolWindowBitmaps .bmp。  例如，可以更改 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico 图标文件添加到 .bmp 布局和重命名为 DSLLanguageName \\DslPackage\\Resources\\ModelExplorerToolWindowBitmaps .bmp。  ，它与 **解决方案资源管理器**时，控件停靠到位生成的设计器将显示在编辑器中资源管理器的选项的此图标。  
  
## 设置在资源管理器节点的自定义图标  
 通过使用资源管理器节点集，可以自定义在编辑器中资源管理器的节点。  下面的过程演示如何将图标添加节点。  
  
#### 将图标添加资源管理器节点  
  
1.  使用任务流解决方案模板，创建一个 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 解决方案。  
  
2.  放在解决方案的 **DSL \\Resources** 文件夹中包含一个 16x16 像素的图标的 .bmp 文件。  
  
3.  在 **DSL 资源管理器**，右击 **资源管理器行为** 然后单击 **添加新资源管理器节点集**。  
  
     **ExplorerNodeSettings** 节点显示在 **自定义节点集** 节点下。  
  
4.  选择的 **ExplorerNodeSettings**，然后在 **属性** 窗口中，将 **类** 到 **参与者**。  
  
5.  设置 **显示的图标** 到图标文件的路径。  
  
6.  转换所有模板，然后生成并运行解决方案。  
  
7.  在编辑器中生成的设计器，请打开示例关系图。  
  
     Explorer 应当显示具有图标的三个 **参与者** 节点。  
  
> [!NOTE]
>  如果您设置的位生成的资源管理器中显示的任何元素的一个节图标，所有资源管理器节点将显示图标。  如果图标尚未设置，节点将显示默认图标。  
  
## 将资源管理器的节点中显示的名称  
 可以更改模型元素的名称如何在编辑器中资源管理器中显示。  下面的过程演示如何显示由注释节点的注释引用任务的名称。  
  
#### 显示属性  
  
1.  打开在前面的过程创建的解决方案。  
  
2.  确保注释通过设置角色的重数引用唯一字段类与属性名称 **主题** 到 0..1。  属性名称应成为 **主题**，并且，关系名称应成为 **CommentReferencesSubject**。  
  
3.  在 **DSL 资源管理器**，右击 **资源管理器行为** 然后单击 **添加新资源管理器节点集**。  
  
     **ExplorerNodeSettings** 节点显示在 **自定义节点集** 节点下。  
  
4.  选择的 **ExplorerNodeSettings**，然后在 **属性** 窗口中，将 **类** 到 **注释**。  
  
5.  右击 **注释** 节点，然后单击 **添加新的属性路径**。  
  
     名为 **显示的属性**的新显示节点。  
  
6.  选择的 **显示的属性**，然后在 **属性** 窗口中，单击 **属性中的路径**的值字段。  选择 **注释**，然后 **CommentReferencesSubject**，然后 **FlowElement**。  发生的路径应类似于 **CommentReferencesSubject.Subject\/\! 主题**。  
  
7.  在 **属性**的值字段中，选择 **名称**。  
  
8.  转换所有模板，然后生成并运行解决方案。  
  
9. 在编辑器中生成的设计器，请打开示例关系图。  
  
10. 绘制 **注释连接** 在注释元素和 **Task1** 元素之间在关系图上。  
  
     资源管理器的节点应显示注释作为 **Task1**。  
  
## 隐藏的节点  
 可以在一个隐藏资源管理器节点通过将其路径。 **DSL 资源管理器**的 **隐藏的节点** 节点。  下面的过程演示如何隐藏注释节点。  
  
#### 隐藏资源管理器节点  
  
1.  打开在前面的过程创建的解决方案。  
  
2.  在 **DSL 资源管理器**，右击 **资源管理器行为** 然后单击 **添加新字段路径**。  
  
     **域路径** 节点显示在 **隐藏的节点**下。  
  
3.  选择的 **域路径**，然后在 **属性** 窗口中，单击 **路经定义**的值字段。  选择 **流向图**，然后 **FlowGraphHasComments**。  发生的路径应类似于 **FlowGraphHasComments.Comments**  
  
4.  转换所有模板，然后生成并运行解决方案。  
  
5.  在编辑器中生成的设计器，请打开示例关系图。  
  
     此时将资源管理器应仅公开 **参与者** 节点，不应显示 **注释** 节点。  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)