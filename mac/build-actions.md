---
title: "生成操作"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="build-actions"></a>生成操作 

Visual Studio for Mac 中的所有文件都有一个生成操作，用于控制生成过程中对文件执行的操作。 可通过右键单击任意文件并浏览到“生成操作”对其进行设置，如下所示：

![](media/projects-and-solutions-image1.png)

C# 项目的一些常见生成操作为：

* **无** - 文件不属于任何一种生成 - 它包括在项目中只是为了便于从 IDE 轻松访问。
* **编译** - 文件将被传递到 C# 编译器作为源文件。
* **嵌入式资源** - 文件将被传递到 C# 编译器作为嵌入程序集中的资源。 然后可使用 `System.Reflection` 命名空间从程序集中读取该文件。
* **内容** - 对于 ASP.NET 项目，将在部署站点时包含这些文件，作为站点的一部分。 对于 Xamarin.iOS 和 Xamarin.Mac 项目，它们会被包含在应用程序包中。

可在解决方案资源管理器中选择多个文件，这样便可同时设置多个文件的生成操作。

此外，还有针对特定项目的生成操作。 例如，Xamarin.iOS 项目具有 BundeledResource 生成操作，用于将文件添加为应用程序包的一部分。 有关 Xamarin.Android 特定生成操作的信息，请参阅 developer.xamarin.com 上的[生成过程](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions)指南。