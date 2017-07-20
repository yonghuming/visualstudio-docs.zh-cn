---
title: "升级 Dotfuscator Community Edition (CE) | Microsoft Docs"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保护, 社区版, 混淆, .NET, 免费, Visual Studio 2017, 升级, 命令行"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: "了解如何升级 Visual Studio 2017 中包含的免费 Dotfuscator Community Edition。"
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
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
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: zh-cn
ms.lasthandoff: 06/23/2017

---

# 升级 Dotfuscator Community Edition (CE)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

Dotfuscator Community Edition (Dotfuscator CE) 直接向使用 Microsoft Visual Studio 的所有开发人员提供许多应用程序保护和强化功能。
升级 Dotfuscator 版本的用户还可使用更多功能。

## 注册 Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Dotfuscator CE 的注册用户可以访问其他功能（如[命令行支持][cli]），将 Dotfuscator CE 轻松集成到自动生成过程中。

注册快速、简单而且免费。
若要注册 Dotfuscator CE，请参阅[完整 Dotfuscator CE 用户指南“入门”页上的“注册 Dotfuscator CE”部分][register-ce]。

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

虽然 Dotfuscator Community Edition 提供了基本级别的保护，但 **_PreEmptive Protection - Dotfuscator_ Professional Edition** 包含增强的模糊处理转换和保护功能。
其中包括:

* 知识产权保护
  * 其他重命名选项，包括 Enhanced Overload Induction™ 和随机标识符选择。
  * 用于解码经过模糊处理的堆栈跟踪的工具。
  * 访问企业级模糊处理转换，包括[以破坏自动化代码反编译为目标的转换][control-flow]。
  * 能够[隐匿敏感字符串][string-encryption]因此不可能对反编译代码进行简单搜索。
  * 能够[将所有权和分发字符审慎串嵌入程序集][watermarking]（软件水印），因此可以确定未经授权的软件泄漏的根源。
  * 能够[将多个程序集组合成一个][linking]，不再分离关注点，让攻击者更加难以确定代码元素的角色。
  * 能够[自动删除应用程序中未使用的代码][pruning]，减少附带的敏感代码量。
* 应用程序完整性保护
  * 其他[应用程序防御行为][check-actions]。
  * 能够将防篡改和反调试代码注入 `.dll` 程序集。
  * 能够在应用程序生命周期截止前提供警告期。
  * 能够在生命周期警告期内或在截止时间后通知应用程序代码。
  * 遥测加密。
* 应用程序监视
  * 能够收集并保存在临时网络中断期间收集的信息。
  * 能够收集可识别个人身份的信息。
  * 能够无限制使用[功能跟踪][features]。
  * 能够跟踪代码捕获和引发的异常以及未处理的异常。
  * 能够跟踪 `.dll` 程序集中的异常。
  * 遥测加密。

Dotfuscator Professional 是行业标准的 [.NET 模糊处理程序][ net-obfuscator]，适用于需要持续支持、维护和产品更新的企业开发人员。
此外，Dotfuscator Professional 提供与 Visual Studio 的更紧密集成，并获得商业使用许可。

有关 Dotfuscator Professional 的高级应用程序保护功能的详细信息，请访问 PreEmptive Solutions 的 [Dotfuscator 概述页][ product-about]和[将其与 Community Edition 进行比较][product-compare]。
[可在 preemptive.com 申请有全面支持的试用版][eval]。

## 另请参阅
<a id="see-also" class="xliff"></a>

[完整 Dotfuscator CE 用户指南中的本主题][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html

