---
title: "一个或多个项目转换失败。 现在，这些项目将被卸载，并在解决方案资源管理器中标记为“不可用”。 重新加载这些项目以确定原因。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 一个或多个项目转换失败。 现在，这些项目将被卸载，并在解决方案资源管理器中标记为“不可用”。 重新加载这些项目以确定原因。
你已尝试打开包含使用 Visual Studio 早期版本创建的一个或多个项目的解决方案。 无法进行转换的某些项目在解决方案资源管理器中将被标记为“不可用”。 必须先将这些项目转换为当前格式，才能打开和编辑你的解决方案，并且才能在你的计算机上安装的 Visual Studio 版本中使用修复的项目。  
  
### 响应此消息  
  
1.  单击“是”，关闭对话框。  
  
     无法转换的项目在解决方案资源管理器中标记为“不可用”。  
  
2.  重新加载无法转换的项目。  
  
    1.  在解决方案资源管理器中，选择活动解决方案中标记为“不可用”的每个项目。  
  
    2.  在“项目”菜单上，选择“重新加载项目”。  
  
3.  仔细查看显示有关项目问题信息的错误消息。 可能的问题包括：  
  
    1.  项目为只读。 不能转换只读项目。 这些项目只能由具有其编辑权限的用户转换。  
  
    2.  项目已被另一用户以独占方式签出。 你必须等到该用户将项目签入后才能将其签出。  
  
    3.  无法从网络服务器签出项目。 确认网络条件，然后重试。  
  
    4.  项目已损坏，必须重新生成。  
  
4.  当你尝试重新加载标记为“不可用”的项目时，处理指示的问题。  
  
5.  重新打开，转换这些项目。 你可能希望在转换项目文件前先备份其副本。  
  
    > [!NOTE]
    >  转换某些项目类型（如 Visual C\+\+ 项目）时，以前的项目文件用文件扩展名 .old 标记并保存在项目目录中。  
  
 如果你是开发团队的成员，应确保从事项目开发的所有人员在他们的本地计算机上安装相同版本的 Visual Studio。 为确保项目保持可访问状态，请定期与开发团队的其他成员进行沟通。  
  
> [!CAUTION]
>  如果解决方案中的项目存储在源代码控件下，而你打算将转换后的项目签人，请首先确定其他解决方案是否共享这些项目。 请勿签入仍在未转换解决方案中使用的已转换项目。 否则会中断这些解决方案中的依赖项，使它们不能正确打开或生成。  
  
## 请参阅  
 [NIB：如何：卸载并重新加载项目](http://msdn.microsoft.com/zh-cn/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-cn/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)