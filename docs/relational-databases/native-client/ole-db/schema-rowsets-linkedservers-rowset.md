---
title: "LINKEDSERVERS 行集 (OLE DB) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c612665a38ec016208d241396a615db2fefa358f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="schema-rowsets---linkedservers-rowset"></a>架构行集-LINKEDSERVERS 行集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  **LINKEDSERVERS**行集枚举组织数据源可以参与[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]分布式查询。  
  
 **LINKEDSERVERS**行集包含以下各列。  
  
|列名|类型指示符|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|链接服务器的名称。|  
|SVR_PRODUCT|DBTYPE_WSTR|标识由链接服务器的名称所表示的数据存储的类型的制造商或其他名称。|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|用于从服务器使用数据的 OLE DB 访问接口的友好名称。|  
|SVR_DATASOURCE|DBTYPE_WSTR|用于从提供程序获得数据源的 OLE DB DBPROP_INIT_DATASOURCE 字符串。|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|用于从提供程序获得数据源的 OLE DB DBPROP_INIT_PROVIDERSTRING 值。|  
|SVR_LOCATION|DBTYPE_WSTR|用于从提供程序获得数据源的 OLE DB DBPROP_INIT_LOCATION 字符串。|  
  
 行集按 SRV_NAME 排序，并支持对 SRV_NAME 的单个限制。  
  
## <a name="see-also"></a>另请参阅  
 [架构行集支持 &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  