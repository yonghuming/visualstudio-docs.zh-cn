---
title: "如何：进行模板的故障排除 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 模板, 疑难解答"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：进行模板的故障排除
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果在开发环境中加载模板失败，有几种方法可以找出问题。  
  
## 验证 .vstemplate 文件  
 如果模板中的 .vstemplate 文件不遵循 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模板架构，则**“新建项目”**对话框中可能不会显示该模板。  
  
#### 验证 .vstemplate 文件  
  
1.  找到包含该模板的 .zip 文件。  
  
2.  解压缩该 .zip 文件。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的**“文件”**菜单上单击**“打开”**，再单击**“文件”**。  
  
4.  选择模板的 .vstemplate 文件，然后单击**“打开”**。  
  
5.  验证 .vstemplate 文件的 XML 是否遵循 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模板架构。  有关 .vstemplate 架构的更多信息，请参见 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)。  
  
    > [!NOTE]
    >  要在创作 .vstemplate 文件时获得 IntelliSense 支持，请将 `xmlns` 特性添加到 `VSTemplate` 元素中，并为其赋值 http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005。  
  
6.  保存并关闭 .vstemplate 文件。  
  
7.  选择模板中包含的文件，右击鼠标，选择**“发送到”**，然后单击**“压缩\(zipped\)文件夹”**。  所选的文件被压缩为一个 .zip 文件。  
  
8.  将新的 .zip 文件与旧的 .zip 文件放在同一目录中。  
  
9. 删除解压缩的模板文件和旧的 .zip 模板文件。  
  
## 监视事件日志  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 记录在处理模板 .zip 文件时遇到的错误。  如果**“新建项目”**对话框中无法按预期显示模板，则可以使用**“事件查看器”**来排查问题。  
  
#### 在“事件查看器”中查找模板错误  
  
1.  在 Windows 中，单击**“开始”**，再单击**“控制面板”**，双击**“管理工具”**，再双击**“事件查看器”**。  
  
2.  在左窗格中单击**“应用程序”**。  
  
3.  查找**“源”**值为 `Visual Studio - VsTemplate` 的事件。  
  
4.  双击某一模板事件以查看错误。  
  
## 请参阅  
 [自定义模板](../ide/customizing-project-and-item-templates.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)