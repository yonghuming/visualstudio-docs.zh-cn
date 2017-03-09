---
title: "解决方案 &lt;name&gt; 及其项目必须转换为当前格式。 | Microsoft Docs"
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
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 解决方案 &lt;name&gt; 及其项目必须转换为当前格式。
你打开的解决方案是用 Visual Studio 的早期版本创建的。 解决方案和项目文件必须转换为当前格式，才能用你计算机上安装的 Visual Studio 版本打开和编辑解决方案。 你可以选择是否立即转换此解决方案。 格式转换不能撤消。  
  
> [!CAUTION]
>  如果解决方案存储在源代码管理下，而你打算重新签入转换后的解决方案，请首先确定是否有其他解决方案共享此解决方案的任何项目。 如果某解决方案的已转换项目仍在被其他未转换的解决方案所使用，则不要签入该解决方案。 否则会中断这些解决方案中的依赖项，使它们不能正确打开或生成。  
  
 你可能希望在转换解决方案和项目文件之前先备份它们。  
  
> [!NOTE]
>  转换 Visual Studio 解决方案后，以前的解决方案文件用文件扩展名“.old”标记并保存在顶级解决方案目录中。 转换某些项目类型（如 Visual C\+\+ 项目）时，以前的项目文件同样用文件扩展名“.old”标记并保存在项目目录中。  
  
 不能转换只读项目。 这些项目只能由具有其编辑权限的用户转换。 必须先将项目的项目文件转换为当前格式，然后才能在已转换的解决方案中使用该项目。 转换解决方案或它的任何项目后，就不能再在以前版本的 Visual Studio 中编辑、生成或运行该解决方案了。  
  
### 响应此消息  
  
1.  选择“是”或“否”。  
  
    -   **是** — 解决方案文件和它的可编辑项目的文件都转换为你计算机上安装的 Visual Studio 版本所用的格式。 如果已转换的解决方案存储在源代码管理下，它将被签出到本地驱动器并打开以进行编辑。  
  
    -   **否** — 解决方案及其项目不转换，也不从源代码管理中签出和打开。  
  
 如果你是开发团队的成员，应确保从事解决方案开发的所有人员在他们的本地计算机上安装相同版本的 Visual Studio。 为确保解决方案和项目保持可访问状态，请你定期与开发团队的其他成员进行沟通。  
  
## 请参阅  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-cn/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)