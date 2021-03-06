---
title: 数据库引擎扩展存储过程编程 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a8e404c4673ccaa55dae0ffb66b381599f7b9d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845555"
---
# <a name="database-engine-extended-stored-procedure-programming"></a>数据库引擎扩展存储过程编程
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] 请改用 CLR 集成。 有关详细信息，请参阅[公共语言运行时 (CLR) 集成编程概念](../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 扩展存储过程 API 提供用于扩展 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能的基于服务器的应用程序编程接口 (API)。 此 API 由用于生成应用程序的 C 和 C++ 函数以及宏组成，分为扩展存储过程和网关应用程序两个类别。  
  
 使用扩展存储过程可以用编程语言（例如 C）创建自己的外部例程。扩展存储过程对于用户的显示方式和执行方式与典型存储过程相同。 可以将参数传递给扩展存储过程，而且扩展存储过程可以返回结果和状态。  
  
## <a name="in-this-section"></a>本节内容  
 [编写扩展存储过程](../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 说明如何创建、管理和使用扩展存储过程。  
  
 [扩展存储过程程序员参考](../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 包含扩展存储过程 API 的参考主题。  
  
  
