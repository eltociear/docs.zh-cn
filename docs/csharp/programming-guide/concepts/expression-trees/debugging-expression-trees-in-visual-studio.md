---
title: 在 Visual Studio 中调试表达式树 (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: cf1708d1155e48d8609baca2067baa66dae08c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169683"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>在 Visual Studio 中调试表达式树 (C#)
可以在调试应用程序时分析表达式树的结构和内容。 要快速了解表达式树结构，可以使用 `DebugView` 属性，该属性[使用特殊语法](debugview-syntax.md)表示表达式树。 （请注意，`DebugView` 仅在调试模式下可用。）  

![VS 调试器中的表达式树的 DebugView 屏幕截图。](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

由于 `DebugView` 是一个字符串，因此可以使用[内置文本可视化工具](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)在多行中进行查看，方法是从  **标签旁边的放大镜图标中选择“文本可视化工具”** `DebugView`。

 ![应用于 DebugView 结果的文本可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

或者，可以为表达式树安装和使用[自定义可视化工具](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)，例如：

- [可读表达式](https://github.com/agileobjects/ReadableExpressions)（[MIT 许可证](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，可在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) 中获得）将表达式树呈现为 C# 代码：

  ![可读表达式可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [表达式树可视化工具](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)（[MIT 许可证](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)）提供表达式树、其属性和相关对象的图形视图：

  ![表达式树可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>打开表达式树的可视化工具  
  
1. 单击“数据提示”、“监视”窗口、“自动”窗口或“本地”窗口中表达式树旁边显示的放大镜图标     。  

    显示可用的可视化工具列表：

    ![显示从 Visual Studio 中打开可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. 单击要使用的可视化工具。  
  
## <a name="see-also"></a>另请参阅

- [表达式树 (C#)](./index.md)
- [在 Visual Studio 中进行调试](/visualstudio/debugger/debugger-feature-tour)
- [创建自定义可视化工具](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` 语法](debugview-syntax.md)
