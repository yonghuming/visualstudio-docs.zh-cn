---
title: "单元测试入门 - 创建测试计划 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit test plans
ms.assetid: 2171CD69-FBB1-4994-9DCC-3BFFDFD26662
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 576b8b744d24a456c16724cb5ae7e65a73a769db
ms.contentlocale: zh-cn
ms.lasthandoff: 06/02/2017

---
# <a name="get-started-with-unit-testing"></a>单元测试入门

使用 Visual Studio 定义和运行单元测试，使代码保持正常运行、确保代码覆盖率并在客户之前找到错误和缺陷。

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>创建单元测试

创建单元测试并经常运行，确保代码正常运行。

1. 创建单元测试项目。
        
   ![向解决方案添加单元测试项目](media/createunittest1.png)
    
1. 为项目命名。
        
   ![单元测试项目模板](media/createunittest2.png)
  
   项目将添加到解决方案中。
    
   ![解决方案资源管理器中的单元测试项目](media/createunittest5.png)
    
1. 在单元测试项目中，向要测试的项目中添加一个引用。
        
   ![向单元测试项目添加引用](media/createunittest6.png)
    
1. 选择包含待测试代码的项目。
        
   ![选择要添加的引用](media/createunittest7.png)
    
1. 对单元测试进行编码。

   ![将代码添加到单元测试](media/createunittest8.png) 

可使用[创建单元测试](create-unit-tests-menu.md)命令创建单元测试方法存根。
也可使用[不同的单元测试框架](#frameworks)创建不同代码语言的测试。

![使用“创建单元测试”命令](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>运行单元测试

1. 打开测试资源管理器。
        
   ![在“测试”菜单上，打开“测试资源管理器”](media/rununittest1.png) 

1. 运行单元测试。
        
   ![在测试资源管理器中运行单元测试](media/rununittest2.png) 

   在测试资源管理器中，可看到通过或未通过的单元测试。
      
   ![在测试资源管理器中查看单元测试结果](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>查看实时单元测试结果

如果在 Visual Studio 2017 或更高版本中使用 MSTest、xUnit 或 NUnit 测试框架，可在 Visual Studio 用户界面内查看单元测试的实时结果。

1. 从“测试”菜单启用 Live Unit Testing。

   ![启用 Live Unit Testing](media/live-test-results-start.png) 

1. 编写和编辑代码时，请在代码编辑器窗口中查看测试的结果。

   ![指向并单击测试结果指示符](media/live-test-results-ui.png) 

1. 指向并单击测试结果指示符以查看详细信息。

   ![查看测试的结果](media/live-test-results-details.png) 

有关更多详细信息，请参阅 [Visual Studio 中的 Live Unit Testing](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/)。

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>使用 IntelliTest 生成单元测试

当你运行 IntelliTest 时，你可轻松看到哪些测试会失败，并可添加任何必要的代码来修复它们。 你可选择要保存到测试项目中的已生成测试，以提供回归套件。 当你更改代码时，重新运行 IntelliTest，以使生成的测试与你的代码更改同步。 若要了解如何操作，请参阅[使用 IntelliTest 为你的代码生成单元测试](https://docs.microsoft.com/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)。

![使用 IntelliTest 生成单元测试](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>使用测试资源管理器运行单元测试

使用测试资源管理器从 Visual Studio 或第三方单元测试项目中运行单元测试、将测试分组到类别中、筛选测试列表以及创建、保存和运行测试的播放列表。 你还可以调试测试并分析测试性能和代码覆盖率。 若要了解如何操作，请参阅[使用测试资源管理器运行单元测试](https://docs.microsoft.com/visualstudio/test/run-unit-tests-with-test-explorer)。

![使用测试资源管理器运行单元测试](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>使用代码覆盖率确定所测试的代码量

若要确定正在由编码的测试（例如单元测试）实际进行测试的项目代码的比例，则可以使用 Visual Studio 的代码覆盖率功能。 若要有效防止 Bug，测试应作用于或“覆盖”你的大部分代码。 若要了解如何操作，请参阅[使用代码覆盖率确定所测试的代码量](https://docs.microsoft.com/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)。

![使用代码覆盖率确定所测试的代码量](media/codecoverage.png)

## <a name="q--a"></a>问题解答

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks">

</a>
####问：如果我使用其他的单元测试框架，我可以在 Visual Studio 中运行单元测试吗？

答：可以，使用针对该框架的插件，Visual Studio 测试运行程序就能够使用该框架。 以下是部分 [Visual Studio 单元测试框架插件](http://go.microsoft.com/fwlink/?LinkID=246630)。

1. 使用 Visual Studio 的扩展管理器下载插件。
        
   ![使用扩展管理器选择第三方单元测试插件](media/install3rdpartyunittestframeworks1.png) 

1. 从“工具/测试”下的 Visual Studio 库下载插件，或者如果知道插件名称，可搜索该插件。
        
   ![下载插件](media/install3rdpartyunittestframeworks2.png) 

1. 创建类库项目。
        
   ![创建类库项目](media/create3rdpartyunittest1.png) 

   将该项目添加到解决方案中。
    
   ![命名类库项目命名并添加它](media/create3rdpartyunittest3.png) 

1. 在类库项目中，运行 NuGet 安装该插件。

   ![管理 NuGet 程序包以安装插件](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) 是 Visual Studio 的扩展，可用来添加和更新项目使用的库和工具。

1. 安装插件。 如果知道名称，可在线搜索该插件。

   ![安装第三方框架](media/create3rdpartyunittest4.png) 

   框架在项目中得到引用。
        
   ![将第三方单元测试框架的引用添加到解决方案中](media/create3rdpartyunittest6.png) 

1. 在类库项目中，向要测试的项目添加一个引用。
        
   ![添加对项目的引用](media/createunittest6.png) 

1. 选择包含待测试代码的项目。
        
   ![选择要测试的代码项目](media/createunittest7.png) 

1. 对单元测试进行编码。

   ![将代码添加到单元测试](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>另请参阅

* [创建单元测试命令](create-unit-tests-menu.md)
* [使用 IntelliTest 生成测试](generate-unit-tests-for-your-code-with-intellitest.md)
* [使用测试资源管理器运行测试](run-unit-tests-with-test-explorer.md)
* [确定代码覆盖率](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [提高代码质量](improve-code-quality.md)

