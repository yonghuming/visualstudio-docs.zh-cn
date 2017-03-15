---
title: "创建基本的工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, 工具窗口"
  - "工具窗口, 在 IDE 中创建"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 创建基本的工具窗口
工具窗口是常见的 Visual Studio：“解决方案资源管理器”、“任务列表”、“错误列表” 和“输出”窗口都是工具窗口。 所有工具窗口都可以按相同的方式停靠在 IDE 中。 可预测停靠使用户可以高效地管理他们的任务和信息。  
  
 Visual Studio Package 模板将创建一个简单工具窗口的基本实现。  
  
### 若要使用 Visual Studio 包模板创建工具窗口  
  
1.  在**“文件”**菜单上，指向**“新建”**，然后单击**“项目”**。  
  
2.  在“新建项目”对话框中，展开“其他项目类型”，然后单击“扩展性”。  
  
3.  在“模板”窗格中，单击“Visual Studio 包”。  
  
4.  在“位置”框中键入 VSPackage 的文件路径。  
  
5.  在“名称”框中，键入解决方案的名称，然后单击“确定”以启动该模板。  
  
6.  在“选择编程语言”页上选择 C\# 或 Visual Basic。 使模板生成 key.snk 文件，以对程序集进行签名。 或者，单击“浏览”以浏览到你自己的密钥文件。 该模板将生成密钥文件的副本并将其命名为 key.snk。  
  
7.  在“基本 VSPackage 信息”页上指定关于 VSPackage 的任何详细信息或接受默认值。 有关详细信息，请参阅[演练：使用 Visual Studio 包模板创建菜单命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
8.  在“选择 VSPackage 选项”页上，选中工具窗口。  
  
9. 在“工具窗口选项”页上，键入“窗口名称”框中的标题栏的名称。 此名称还用作工具窗口的菜单命令的显示文本。 菜单命令被添加到“视图 ”菜单上的“其他窗口”子菜单中。 在“命令 ID”框中键入工具窗口的命令 ID，或接受默认值。  
  
10. 单击“完成”以在指定的文件夹中创建 VSPackage。  
  
### 若要测试工具窗口  
  
1.  在“视图”菜单上，指向“其他窗口”，然后单击工具窗口命令。 将出现带有“点我\!”按钮的工具窗口。  
  
2.  单击按钮。 文本显示一条消息：  
  
     我们在 \[Company.\<VSPackage name\>.MyControl\].button1\_Click\(\) 内部。  
  
## 请参阅  
 [以编程方式打开工具窗口](../misc/opening-a-tool-window-programmatically.md)   
 [VSPackage 要点](../misc/vspackage-essentials.md)