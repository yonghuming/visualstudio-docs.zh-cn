---
title: "安全性和已本地化的附属程序集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 2bac6b9d00c52e782cf2993ce70c3bd3466aba55
ms.contentlocale: zh-cn
ms.lasthandoff: 05/30/2017

---
# 安全性和已本地化的附属程序集
<a id="security-and-localized-satellite-assemblies" class="xliff"></a>
如果主程序集使用强命名，则必须使用与主程序集相同的私钥对附属程序集进行签名。 如果主程序集和附属程序集之间的公钥/私钥对不匹配，则不会加载资源。 有关对程序集签名的详细信息，请参阅[如何：使用强名称为程序集签名](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)。  
  
 通常，可能需要要求你组织的签名组或外部签名组织使用私钥进行签名。 这是因为私钥具有敏感性：访问通常限制为少数几个人。 可以在开发期间使用延迟签名。 有关详细信息，请参阅[延迟为程序集签名](/dotnet/framework/app-domains/delay-sign-assembly)。  
  
## 另请参阅
<a id="see-also" class="xliff"></a>  
 [程序集安全注意事项](/dotnet/framework/app-domains/assembly-security-considerations)   
 [秘钥安全性概念](/dotnet/standard/security/key-security-concepts)   
 [基于 .NET Framework 的国际应用程序简介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [本地化应用程序](../ide/localizing-applications.md)   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)
