---
title: "MSBuild 错误 MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3482
**MSB3482：签名时出错：“\<error\>”**  
  
 当使用 ClickOnce 部署发布或使用 SignTool 对清单签名时，可能会遇到由 SignTool 生成的此错误。 这里列出了常见的问题。  
  
 **签名时出错：值不能为 null。 参数名称：strongNameKey'。**  
  
 此错误在 ClickOnce 部署过程中可能会出现在错误列表中。 选择无效的签名密钥就会导致此问题。 通常你会尝试使用非 RSA 加密密钥。 SignTool 仅支持 RSA 密钥加密。  
  
 若要更正此错误，需要获得启用了代码签名的 RSA 加密密钥。  
  
 **签名时出错：“无法对受信任的根证书颁发机构建立证书链。”**  
  
 此错误在 ClickOnce 部署过程中可能会出现在错误列表中。 问题在于，证书拥有的链或根颁发机构在用户的计算机上不受信任。 在计算机之间移动证书\/密钥后通常会发生这种情况。  
  
 若要更正此错误，请安装由证书颁发机构 \(CA\) 创建的“根证书”。 通常情况下，可以转到 CA 供应商的网站并根据需要再次下载。  
  
 **签名时出错：对 …\\setup.exe 签名失败。 SignTool 错误：ISignCode::Sign 返回了错误：0x80880253 签名者的证书对签名无效。**  
  
 此错误在 ClickOnce 部署过程中可能会出现在错误列表中。  
  
 此问题很可能是由于证书已超出有效日期，例如，你的证书已过期。  
  
 若要更正此错误，请获取未超过有效日期的更新后的证书。  
  
 有关如何更新证书，请参阅文章 925521，“在用于登录安装的证书过期后，你尝试更新 Visual Studio 2005 ClickOnce 应用程序时，会收到一条错误消息”，该文章位于 Microsoft 知识库[http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521)。  
  
 **键集不存在。**  
  
 可能 .pfx 文件和证书之间不匹配。 请尝试删除并重新安装该证书，和\/或重新创建 .pfx 文件。  
  
 **该项不适于在指定状态下使用**  
  
 请参阅 http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx  
  
 **参数不正确。**  
  
 你的生成是在服务中运行还是在导入证书以外的用户帐户中运行? 请尝试关闭需要私钥保护的任何本地安全策略设置。  接下来，删除并重新导入生成的用户帐户的证书。  
  
 **无法完成请求的操作。  必须信任计算机才可以进行委托，并且必须将当前用户帐户配置为允许委托。**  
  
 请参阅[此 MSDN 博客文章。](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)  
  
## 请参阅  
 [代码签名简介](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe（签名工具）](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [“项目设计器”\-\>“签名”页](../ide/reference/signing-page-project-designer.md)   
 [如何：对程序集签名 \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [如何：使用强名称为程序集签名](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [具有强名称的程序集](../Topic/Strong-Named%20Assemblies.md)   
 [托管应用程序的强名称签名](http://msdn.microsoft.com/zh-cn/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)