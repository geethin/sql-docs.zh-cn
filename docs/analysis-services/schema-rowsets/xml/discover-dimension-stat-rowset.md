---
title: "DISCOVER_DIMENSION_STAT 行集 |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8646303bf73732a1a9f62c94879840e9e9866865
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="discoverdimensionstat-rowset"></a>DISCOVER_DIMENSION_STAT 行集
  提供有关维度的信息，包括维度所在的数据库的名称、维度名称、维度的属性以及每个属性的成员计数。 在表格模型中，这对应于表中的列和每个列中的值数。  
  
 **适用于：**表格模型、 多维模型  
  
## <a name="rowset-columns"></a>行集列  
 **DISCOVER_DIMENSION_STAT**行集包含以下各列。  
  
|列名|类型指示符|限制|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|必需|包含维度的数据库的名称。<br /><br /> 此列在限制列表中是必需的。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|必需|维度的名称。<br /><br /> 此列在限制列表中是必需的。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||维度中的属性的名称。|  
|**ATTRIBUTE_COUNT**|**是 DBTYPE_I8**||命名属性中的值的计数。 对于表格模型，该值始终等于表中的行数值。|  
  
 未对此架构行集进行排序。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 返回行集  
 在使用 ADOMD.NET 和架构行集检索元数据时，可以使用 GUID 或字符串在 GetSchemaDataSet 方法中引用架构行集对象。 有关详细信息，请参阅 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表提供了用于标识此行集的 GUID 和字符串值。  
  
|参数|值|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>另请参阅  
 [XML for Analysis 架构行集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  