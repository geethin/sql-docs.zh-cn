---
title: 在 SQL Server 机器学习中的 Python 库和数据类型 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 384c8c94bdef65e41af999848c9bac63fc0c8d40
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888363"
---
# <a name="python-libraries-and-data-types"></a>Python 库和数据类型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本指南介绍了 SQL Server 机器学习服务 （数据库内） 和 （独立版） 安装附带的 Python 库。

此文章还列出了不支持的数据类型和列表的数据类型的 Python 和 SQL Server 之间传递数据时可能会隐式执行转换。

## <a name="python-version"></a>Python 版本

SQL Server 2017 Anaconda 4.2 分发和 Python 3.6。

RevoScaleR 功能的子集 (rxLinMod，rxLogit，rxPredict，rxDTrees，rxBTrees，也许一些其他) 提供了使用 Python Api、 使用新的 Python 包**revoscalepy**。 此包可用于使用 Pandas 数据帧、 XDF 文件或 SQL 数据查询处理数据。

有关详细信息，请参阅[什么是 revoscalepy？](what-is-revoscalepy.md)。

Python 支持有限的数量的相比于 SQL Server 数据类型。 因此，只要使用从 SQL Server 在 Python 脚本中的数据，数据可能会隐式转换为兼容的数据类型。 但是，通常不能自动执行确切的转换，并且返回错误。

## <a name="python-and-sql-data-types"></a>Python 和 SQL 数据类型

此表列出了所提供的隐式转换。 不支持其他数据类型。

|SQLtype|Python 类型|
|-------|-----------|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|



