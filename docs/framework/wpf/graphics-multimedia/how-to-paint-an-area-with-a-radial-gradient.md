---
title: 如何：使用径向渐变绘制区域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452748"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>如何：使用径向渐变绘制区域
此示例演示如何使用 <xref:System.Windows.Media.RadialGradientBrush> 类来绘制具有径向渐变的区域。  
  
## <a name="example"></a>示例  
 下面的示例使用 <xref:System.Windows.Media.RadialGradientBrush> 绘制一个矩形，该矩形具有从黄色转换为红色到浅绿色的径向渐变。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 下图显示了前面示例的渐变。 渐变的停止点已突出显示。  
  
 ![径向渐变中的渐变停止点](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> 本主题中的示例使用默认坐标系统来设置控制点。 默认坐标系与边界框相关：0指示边界框的0%，1指示边界框的100%。 您可以通过将 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 属性设置为 <xref:System.Windows.Media.BrushMappingMode.Absolute>值来更改此坐标系统。 绝对坐标系与范围框无关。 值直接在本地空间中解释。  
  
 有关其他 <xref:System.Windows.Media.RadialGradientBrush> 示例，请参阅[画笔示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 有关渐变和其他类型画笔的详细信息，请参阅[采用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)。
