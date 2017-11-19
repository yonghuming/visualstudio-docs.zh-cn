---
title: "自定义 Visual Studio 如何创建数据绑定控件的标题 |Microsoft 文档"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 86f0e451fe81875868db0d6ddcd9cead790800d3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自定义 Visual Studio 如何创建数据绑定控件的标题
当拖动项时从[数据源窗口](add-new-data-sources.md)拖到设计器，特别注意派上用场： 标题标签中的列名称重新格式化为一个更具可读性的字符串，当两个或更多的单词发现连接在一起。 你可以自定义创建的方式在其中这些标签，通过设置**SmartCaptionExpression**， **SmartCaptionReplacement**，和**SmartCaptionSuffix**中的值**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data 设计器**注册表项。  
  
> [!NOTE]
> 在创建之前，此注册表项不存在。  
  
智能标题输入到的值的正则表达式由控制**SmartCaptionExpression**值。 添加**数据设计器**注册表项重写默认正则表达式，用于控制标题标签。 有关正则表达式的详细信息，请参阅[Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
下表介绍控制标题标签的注册表值。  
  
|注册表项|描述|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|用于与您的模式匹配的正则表达式。|  
|**SmartCaptionReplacement**|要显示在匹配任何组的格式**SmartCaptionExpression**。|  
|**SmartCaptionSuffix**|要追加到的标题末尾一个可选的字符串。|  
  
下表列出这些注册表值的内部默认设置。  
  
|注册表项|默认值|说明|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124; _ +|匹配大写字符或下划线后跟一个小写字符。|  
|**SmartCaptionReplacement**|$1 $2|$1 表示匹配的第一个表达式的括号内的任意字符，$2 表示匹配的第二个括号内的任意字符。 替代功能第一个匹配项、 空格和第二个匹配项。|  
|**SmartCaptionSuffix**|:|将字符追加到返回的字符串表示。 例如，如果标题是`Company Name`，后缀便`Company Name:`|  
  
> [!CAUTION]
> 你应执行任何操作在注册表编辑器时请格外小心。 编辑它之前备份注册表。 如果没有正确使用注册表编辑器，你可能会导致严重的问题，可能需要重新安装操作系统。 Microsoft 不保证可以解决通过注册表编辑器使用不当导致的问题。 使用注册表编辑器的风险由您自己承担。  
>   
>  以下知识库文章包含有关备份、 编辑和还原注册表的说明：[的 Microsoft Windows 注册表说明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)(http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>若要修改的数据源窗口的智能标题行为  
  
1.  通过单击打开命令窗口**启动**然后**运行**。  
  
2.  类型`regedit`中**运行**对话框中，单击**确定**。  
  
3.  展开**HKEY_CURRENT_USER**，**软件*， **Microsoft**， **VisualStudio**节点。  
  
7.  右键单击**15.0**节点，然后创建一个新**密钥**名为`Data Designers`。  
  
8.  右键单击**数据设计器**节点，并创建三个新的字符串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 右键单击**SmartCaptionExpression**值，然后选择**修改**。  
  
12. 输入所需的正则表达式**数据源**窗口来使用。  
  
13. 右键单击**SmartCaptionReplacement**值，然后选择**修改**。  
  
14. 输入替换字符串格式设置你想要显示在正则表达式中匹配的模式的方式。  
  
15. 右键单击**SmartCaptionSuffix**值，然后选择**修改**。  
  
16. 输入你想要显示的标题末尾任何的字符。  
  
    下一次拖动项时从**数据源**窗口中，创建标题标签使用提供的新注册表值。  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>若要关闭智能的隐藏字幕功能  
  
1.  通过单击打开命令窗口**启动**然后**运行**。  
  
2.  类型`regedit`中**运行**对话框中，单击**确定**。  
  
3.  展开**HKEY_CURRENT_USER**，**软件**， **Microsoft**， **VisualStudio**节点。  
  
7.  右键单击**15.0**节点，然后创建一个新**密钥**名为`Data Designers`。  
  
8.  右键单击**数据设计器**节点，并创建三个新的字符串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 右键单击**SmartCaptionExpression**项，然后选择**修改**。  
  
12. 输入`(.*)`的值。 这与匹配的整个字符串。  
  
13. 右键单击**SmartCaptionReplacement**项，然后选择**修改**。  
  
14. 输入`$1`的值。 这将替换匹配的值，该值是整个字符串，以便它将保持不变的字符串。  
  
    下一次拖动项时从**数据源**标题标签窗口中，创建的未修改的标题。  
  
## <a name="see-also"></a>另请参阅  
[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)