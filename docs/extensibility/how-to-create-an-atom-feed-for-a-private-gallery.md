---
title: "如何： 创建 Atom 馈送为专用库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b41cb3012b937ac5448b129657064cca68a5d725
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>如何： 创建 Atom 馈送为专用库
你可以创建 Atom (RSS) 源到 intranet 位置包含扩展并添加到源**扩展和更新**作为专用库。 有关详细信息，请参阅[私有库](../extensibility/private-galleries.md)。  
  
## <a name="creating-an-atom-feed"></a>创建 Atom 馈送  
 若要创建 Atom 馈送作为专用库，你首先收集有关你的扩展 （.vsix 文件） 到一个文件夹。 可以将它们添加到子文件夹如果你想。 你将需要以下资源：  
  
-   使扩展作为专用库可用 atom.xml 文件。 有关如何连接到的 atom.xml 文件信息**扩展和更新**，请参阅[私有库](../extensibility/private-galleries.md)。  
  
-   包含已从扩展 （例如，屏幕快照） 中提取任何图像文件的文件夹。 Atom.xml 文件包含这些图像的相对链接，以便在提供了**扩展和更新**。  
  
 例如，假定你已经以下两种扩展收集到文件夹：  
  
-   Template_Wizard_239.vsix，这是一个空的 VSIX 项目模板。  
  
-   SelectionHighlight.vsix，是一种工具以突出显示所选单词的所有实例。  
  
 Atom.xml 文件的内容类似于下面的示例：  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ....</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  ...  
  </entry>  
  </feed>  
  
```  
  
 请注意两个链接标记引用的映像的生成文件夹中的屏幕截图。  
  
## <a name="see-also"></a>另请参阅  
 [专用库](../extensibility/private-galleries.md)