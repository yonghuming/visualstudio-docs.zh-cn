---
title: "Visual Studio 中的 Python入门 | Microsoft Docs"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
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
translationtype: Human Translation
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0

---
# <a name="getting-started-with-python-in-visual-studio"></a>Visual Studio 中的 Python 入门

Python ([http://python.org/download/](http://python.org/download/)) 是一个受欢迎的编程语言，它可靠、灵活、易于学习、免费使用，并且强大的开发人员社区和很多免费库都支持它。 Python 可在所有主要的操作系统上使用，并且可用于多种用途，包括 Web 应用程序、web 服务、桌面应用程序、脚本编写和科学计算。 因此许多大学、科学家、非正式的开发人员和专业开发人员都使用 Python。

若要了解该语言的详细信息，请从 [Python for Beginners](https://www.python.org/about/gettingstarted/)（面向初学者的 Python）(python.org) 开始了解。

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio

Python Tools for Visual Studio (PTVS) 是 Visual Studio 的免费、开源扩展功能，它提供强大的 Python 开发体验，包括项目系统和模板、丰富的编辑和 IntelliSense、全功能调试和各种其他工具。

此扩展具有以下功能：

- 支持多种解释器：各种版本的 CPython、IronPython 以及 IPython
- 项目系统可隐式选取 Python 代码的文件夹结构，也允许显式控制，以便于你标识应用代码、测试代码、网页、JavaScript、生成脚本等等。
- 用于控制台、Web、Azure、数据科学和其他类型项目的项目模板。
- 丰富的编辑和代码理解功能，包括语法着色、跨所有代码和库的自动完成功能、签名帮助、类视图、转到定义、查找所有引用、重构等等。
- 交互式 (REPL) 窗口
- 丰富的无需 Visual Studio 项目的调试功能，包括可对现有可执行文件进行调试、混合模式调试、对 Windows/Linux/Mac 进行远程调试，以及在交互式窗口中进行调试。

- 使用数据可视化功能的 IPython。
- 支持 IronPython 和 .NET/WPF。
- 分析工具。
- 测试工具。
- [Azure SDK for Python](#azure-sdk-for-python)

下列资源可帮你入门：

- [安装 Python Tools for Visual Studio](https://www.visualstudio.com/vs/python/)
- [安装指南](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [入门和深入了解短片](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- 安装和功能演示（27 分钟）](https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [文档](https://github.com/Microsoft/PTVS/wiki)
- [源代码](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python 支持 Windows、Mac 和 Linux，使得使用和管理 Microsoft Azure 服务更加方便。 请参阅下列资源了解详细信息：

- 若要安装 SDK，请使用 [Python 软件包索引](https://pypi.python.org/pypi/azure)或者按照 Azure 文档中的[安装 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) 的说明进行操作。
- [Azure SDK for Python 开发人员中心](http://azure.microsoft.com/en-us/develop/python/)通过教程提供许多从安装到文档的帮助。  以下为一些要点：
- 操作指南：
  - [存储 Blob](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [存储队列](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [存储表](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [服务总线队列](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [服务总线主题/订阅](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [服务管理](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- [SDK 的 GitHub 存储库](https://github.com/Azure/azure-sdk-for-python)中的[单元测试](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)也是很好的 API 信息来源。


## <a name="scientific-computing"></a>科学计算
除所有 Python 数据科学家库以外，Python Tools for Visual Studio 也支持 IPython 和 IPython 笔记本（可以在 Azure 中托管）。

我们建议从[加利福尼亚大学欧文分校](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)获取 IPython 和科学计算库（matplotlib、scipy、numpy 等）。

## <a name="see-also"></a>另请参阅
 [PTVS 入门：设置 Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [PTVS 入门：开始编码（项目）](../python/getting-started-with-ptvs-start-coding-projects.md)
 [PTVS 入门：编辑代码](../python/getting-started-with-ptvs-editing-code.md)
 [PTVS 入门：调试](../python/getting-started-with-ptvs-debugging.md)
 [PTVS 入门：交互式 Python](../python/getting-started-with-ptvs-interactive-python.md)
 [PTVS 入门：在 Azure 中构建网站](../python/getting-started-with-ptvs-building-a-website-in-azure.md)


<!--HONumber=Feb17_HO4-->


