---
title: "用于本地化的资源的分层组织 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "资源文件, 已本地化"
  - "本地化 [Visual Studio], 资源"
  - "回调资源"
  - "国际应用程序 [Visual Studio], 存储资源"
  - "附属程序集, 资源层次结构"
  - "全球化 [Visual Studio], 资源"
  - "附属程序集"
  - "资源 [Visual Studio], 回调系统"
  - "资源文件，回退进程"
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>用于本地化的资源的分层组织
在 Visual Studio 中，本地化资源（适用于各区域性的字符串和图像等数据）存储在单独的文件中并根据 UI 区域性设置进行加载。 若要了解本地化资源是如何加载的，可以将其想象成按层次结构的方式进行组织。  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>层次结构中的资源种类  
  
-   层次结构的顶部是用于默认区域性（例如英语 ("en")）的回退资源。 这些是唯一不具有自有文件的资源；它们存储在主程序集中。  
  
-   回退资源下方是任何非特定区域性的资源。 非特定区域性与一种语言而非国家/地区相关联。 例如，法语 ("fr") 是一个非特定区域性。 （请注意，回退资源也用于非特定区域性，但用于特殊的非特定区域性。）  
  
-   非特定区域性资源下方是任何特定区域性的资源。 特定区域性与一种语言而非国家/地区相关联。 例如，加拿大法语 ("fr-CA") 是一个特定区域性。  
  
 如果一个应用程序尝试加载任何本地化资源，例如一个字符串，且未找到它，则会搜索整个层次结构，直到找到包含所请求的资源的资源文件为止。  
  
 存储资源的最佳方式是尽可能将资源一般化。 也就是说，尽可能将本地化的字符串、图像等存储在非特定区域性的资源文件中，而不是特定区域性的资源文件中。 例如，如果你具有比利时法语 ("fr-BE") 区域性的资源以及紧邻英语回退资源且位于其上方的资源，那么如果某人使用一个系统上的应用程序且该系统配置为加拿大法语区域性，则可能会发生问题。 该系统会查找 "fr-CA" 的附属程序集，然后会找不到它，接着会加载包含英语回退资源的主程序集，而不会加载法语资源。 下图显示了存在这种问题的情况。  
  
 ![仅特定资源](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 如果遵循上述建议的做法，即将尽可能多的资源放置在 "fr" 区域性的非特定区域性资源文件中，则加拿大法语用户不会看到为 "fr-BE" 区域性所标记的资源，而是会看到法语字符串。 下面的情况显示了这一建议使用的方案。  
  
 ![NeutralSpecificResources 图](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>另请参阅  
 [用于本地化的非特定资源语言](../ide/neutral-resources-languages-for-localization.md)   
 [安全性和已本地化的附属程序集](../ide/security-and-localized-satellite-assemblies.md)   
 [本地化应用程序](../ide/localizing-applications.md)   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)   
 [如何：为 Windows 窗体全球化设置区域性和用户界面的区域性](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [如何：为 ASP.NET 网页全球化设置区域性和 UI 区域性](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)


<!--HONumber=Feb17_HO4-->


