---
title: SQL Server - Latches 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3b4953b71343dfa5bae3c0622369fb9bf3722c5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145678"
---
# <a name="sql-server-latches-object"></a>SQL Server Latches 对象
  Microsoft **中的** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象提供计数器来监视称为闩锁的内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源锁。 通过监视闩锁来确定用户活动和资源使用情况，将有助于查明性能瓶颈。  
  
 下表介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** 计数器。  
  
|SQL Server Latches 计数器|Description|  
|---------------------------------|-----------------|  
|**Average Latch Wait Time (ms)**|必须等待授予的闩锁请求的平均等待时间（毫秒）。|  
|**Latch Waits/sec**|未能立即授予的闩锁请求数。|  
|**Number of SuperLatches**|目前是 SuperLatch 的闩锁数。|  
|**SuperLatch Demotions/sec**|在上一秒钟内已降级为常规闩锁的 SuperLatch 数。|  
|**SuperLatch Promotions/sec**|在上一秒钟内已提升为 SuperLatch 的闩锁数。|  
|**Total Latch Wait Time (ms)**|上一秒钟内的闩锁请求的总等待时间（毫秒）。|  
  
## <a name="see-also"></a>请参阅  
 [监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md)  
  
  
