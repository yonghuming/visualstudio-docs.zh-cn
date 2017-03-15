---
title: "如何：自定义 Visual Studio 创建数据绑定控件的标题的方式
 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "标题, 数据绑定"
  - "“数据源”窗口, 标签标题"
  - "标签标题, “数据源”窗口"
  - "智能标题"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：自定义 Visual Studio 创建数据绑定控件的标题的方式

将项目从[“数据源”窗口](../Topic/Data%20Sources%20Window.md)拖到 Windows 窗体设计器上时，特别要注意以下事项：当发现两个或更多的单词串联在一起时，标题标签中的列名将重新设置格式为更易读的字符串。  您可以通过在**“HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Data Designers”**注册表项中设置**“SmartCaptionExpression”**、**“SmartCaptionReplacement”**和**“SmartCaptionSuffix”**值来自定义创建这些标签的方法。  
  
> [!NOTE]
>  此注册表项在您创建它之前并不存在。  
  
 智能标题由输入**“SmartCaptionExpression”**值的值的正则表达式控制。  添加**“Data Designers”**注册表项会重写控制标题标签默认正则表达式。  有关正则表达式的更多信息，请参见 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
 下表介绍了控制标题标签的注册表值。  
  
|注册表项|说明|  
|----------|--------|  
|SmartCaptionExpression|用于与您的模式匹配的正则表达式。|  
|SmartCaptionReplacement|显示**“SmartCaptionExpression”**中匹配的所有组的格式。|  
|SmartCaptionSuffix|追加到标题末尾的可选字符串。|  
  
 下表列出了这些注册表值的内部默认设置。  
  
|项|默认值|说明|  
|-------|---------|--------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|与后跟大写字符或下划线的小写字符匹配。|  
|**SmartCaptionReplacement**|$1 $2|$1 表示表达式的第一个括号中匹配的任意字符，$2 表示第二个括号中匹配的任意字符。  替换是第一个匹配、空格，然后是第二个匹配。|  
|**SmartCaptionSuffix**|:|表示追加到返回的字符串的字符。  例如，如果标题为 `Company Name`，则加上后缀使之成为 `Company Name:`|  
  
> [!CAUTION]
>  在注册表编辑器中进行任何操作时均应非常小心。  编辑注册表之前请将其备份。  错误地使用注册表编辑器可导致严重问题（可能需要重新安装操作系统）。  Microsoft 不保证由于错误地使用注册表编辑器导致的问题可以得到解决。  使用注册表编辑器的风险由您自己承担。  
>   
>  以下知识库文章包含有关备份、编辑和恢复注册表的说明：[Description of the Microsoft Windows registry](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)（Microsoft Windows 注册表的说明）\(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### 修改“数据源”窗口的智能标题行为  
  
1.  通过单击**“开始”**然后单击**“运行”**打开命令窗口。  
  
2.  在**“运行”**对话框中键入 `regedit`，然后单击**“确定”**。  
  
3.  展开**“HKEY\_CURRENT\_USER”**节点。  
  
4.  展开**“Software”**节点。  
  
5.  展开**“Microsoft”**节点。  
  
6.  展开**“VisualStudio”**节点。  
  
7.  右击**“10.0”**节点，并创建一个名为 `Data Designers` 的新**“项”**。  
  
8.  右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionExpression` 的新**“字符串值”**。  
  
9. 右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionReplacement` 的新**“字符串值”**。  
  
10. 右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionSuffix` 的新**“字符串值”**。  
  
11. 右击**“SmartCaptionExpression”**项，然后选择**“修改”**。  
  
12. 输入**“数据源”**窗口要使用的正则表达式。  
  
13. 右击**“SmartCaptionReplacement”**项，然后选择**“修改”**。  
  
14. 输入已设置所需格式的替换字符串，使其显示模式与正则表达式中的模式相匹配。  
  
15. 右击**“SmartCaptionSuffix”**项，然后选择**“修改”**。  
  
16. 输入要在标题末尾出现的任意字符。  
  
     当下一次从**“数据源”**窗口拖动某些项时，将使用所提供的新建注册表值创建标题标签。  
  
### 关闭智能标题功能  
  
1.  通过单击**“开始”**然后单击**“运行”**打开命令窗口。  
  
2.  在**“运行”**对话框中键入 `regedit`，然后单击**“确定”**。  
  
3.  展开**“HKEY\_CURRENT\_USER”**节点。  
  
4.  展开**“Software”**节点。  
  
5.  展开**“Microsoft”**节点。  
  
6.  展开**“VisualStudio”**节点。  
  
7.  右击**“10.0”**节点，并创建一个名为 `Data Designers` 的新**“项”**。  
  
8.  右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionExpression` 的新**“字符串值”**。  
  
9. 右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionReplacement` 的新**“字符串值”**。  
  
10. 右击**“Data Designers”**节点，然后创建一个名为 `SmartCaptionSuffix` 的新**“字符串值”**。  
  
11. 右击**“SmartCaptionExpression”**项，然后选择**“修改”**。  
  
12. 为该值输入 `(.*)`。  这将与整个字符串匹配。  
  
13. 右击**“SmartCaptionReplacement”**项，然后选择**“修改”**。  
  
14. 为该值输入 `$1`。  这将替换具有匹配值的字符串，该值是整个字符串，以便该值在替换结果中仍保持不变。  
  
     当下一次从**“数据源”**窗口拖动某些项时，将用未修改的标题创建标题标签。  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)