---
title: 使用 IOpenRowset 创建行集 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0f13332d63fb592238f21b744f9e6c5833659980
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688825"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>使用 IOpenRowset 创建行集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持**iopenrowset:: Openrowset**方法有以下限制：  
  
-   必须在 pTableID 参数指向的数据库 ID (DBID) 结构中指定基表或视图。  
  
-   DBID eKind 成员必须指示 DBKIND_NAME。  
  
-   DBID uName 成员必须将现有基表或视图的名称指定为 Unicode 字符串。  
  
-   OpenRowset 的 pIndexID 参数必须为 NULL。  
  
 IOpenRowset::OpenRowset 的结果集包含单个行集。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 游标可以支持包含单个行集的结果集。 游标支持允许开发人员使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并发控制机制。  
  
## <a name="see-also"></a>请参阅  
 [行集](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
