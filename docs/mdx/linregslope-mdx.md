---
title: LinRegSlope (MDX) |Microsoft 文档
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aa1c24076f76c4f61692deac69741d8cf1557462
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741536"
---
# <a name="linregslope-mdx"></a>LinRegSlope (MDX)


  一组中，线性回归计算，并在回归行中，返回的值的斜率 y = ax + b。  
  
## <a name="syntax"></a>语法  
  
```  
  
LinRegSlope(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *Numeric_Expression_y*  
 返回表示 Y 轴值的数字的有效数值表达式，通常是单元坐标的多维表达式 (MDX)。  
  
 *Numeric_Expression_x*  
 通常是单元坐标（返回代表 X 轴的值的数字）的多维表达式 (MDX) 的有效数值表达式。  
  
## <a name="remarks"></a>Remarks  
 线性回归使用最小二乘法，可以计算出回归线（即一系列点的最佳拟合线）的公式。 回归行都有以下公式，其中是斜率，b 是截距：  
  
 y = ax+b  
  
 **LinRegSlope**函数的计算结果可获取 y 轴的值的第一个数值表达式对指定的集。 然后，此函数根据第二个数值表达式（如果已指定）对指定的集表达式求值，以获取 X 轴的值。 如果未指定第二个数值表达式，则此函数使用指定集中的单元的当前上下文作为 X 轴的值。 与时间维度经常使用未指定的 x 轴自变量。  
  
 获取组点之后, **LinRegSlope**函数返回回归线的斜率 (在前面的等式中)。  
  
> [!NOTE]  
>  **LinRegSlope**函数将忽略空单元格包含文本或逻辑值。 但是，该函数将包含值为零的单元。  
  
## <a name="example"></a>示例  
 下面的示例返回单位销售额和商店销售额度量值的回归线的斜率。  
  
```  
LinRegSlope(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
