---
title: 筛选器 (MDX) |Microsoft 文档
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d740148052712a69a39e0de314496733b3b26a8b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740526"
---
# <a name="filter-mdx"></a>Filter (MDX)


  返回根据搜索条件对指定集进行筛选后得到的集。  
  
## <a name="syntax"></a>语法  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *Logical_Expression*  
 计算结果为 True 或 False 的有效多维表达式 (MDX) 逻辑表达式。  
  
## <a name="remarks"></a>Remarks  
 **筛选器**函数计算对指定集中的每个元组指定的逻辑表达式。 该函数返回由指定集中的其中逻辑表达式的计算结果为每个元组集中**true**。 如果没有元组评估结果为**true**，则返回空集。  
  
 **筛选器**函数工作方式类似于[IIf](../mdx/iif-mdx.md)函数。 **IIf**函数将返回两个选项之一基于 MDX 逻辑表达式的计算，而**筛选器**函数将返回满足指定的搜索条件的元组的一组。 实际上，**筛选器**函数执行`IIf(Logical_Expression, Set_Expression.Current, NULL)`上每个元组中组，并返回生成设置。  
  
## <a name="examples"></a>示例  
 以下示例说明 Filter 函数在查询的行轴上的用法，以便仅返回 Internet Sales Amount 大于 $10000 的 Date：  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Filter function 函数还可以在计算成员定义内部使用。 下面的示例返回的总和`Measures.[Order Quantity]`成员，在某段中包含的 2003 年的第一个九个月聚合`Date`维度，从**Adventure Works**多维数据集。 **PeriodsToDate**函数对其定义元组集中**聚合**函数操作。 **筛选器**函数限制以前的时间段内返回到具有较低值 Reseller Sales Amount 度量值的这些元组。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
