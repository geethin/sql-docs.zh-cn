---
title: 配置 Distributed 的 Replay |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: aee11dde-daad-439b-b594-9f4aeac94335
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5253fc1b7ace718fc2d83cadd9fca944b4898c7b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52506220"
---
# <a name="configure-distributed-replay"></a>Configure Distributed Replay
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播配置详细信息在分布式重播控制器、客户端以及安装有管理工具的位置的 XML 文件中指定。 这些文件包括下面的文件：  
  
-   [控制器配置文件](#DReplayController)  
  
-   [客户端配置文件](#DReplayClient)  
  
-   [预处理配置文件](#PreprocessConfig)  
  
-   [重播配置文件](#ReplayConfig)  
  
##  <a name="DReplayController"></a> 控制器配置文件：DReplayController.config  
 当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播控制器服务启动时，它将从控制器配置文件 `DReplayController.config`加载日志记录级别。 此文件位于安装有分布式重播控制器服务的文件夹内：  
  
 \<控制器安装路径>\DReplayController.config  
  
 控制器配置文件指定的日志记录级别包括：  
  
|设置|XML 元素|描述|允许的值|Required|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|日志记录级别|`<LoggingLevel>`|为控制器服务指定日志记录级别。|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|否。 默认情况下，该值为 `CRITICAL`。|  
  
### <a name="example"></a>示例  
 本示例显示一个控制器配置文件，该文件已经过修改以便消除 `INFORMATION` 和 `WARNING` 日志条目。  
  
```  
<?xml version='1.0'?>  
<Options>  
<LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="DReplayClient"></a> 客户端配置文件：DReplayClient.config  
 当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播客户端服务启动时，它将从客户端配置文件 `DReplayClient.config`加载配置设置。 此文件位于每台客户端上安装有分布式重播客户端服务的文件夹内：  
  
 \<客户端安装路径>\DReplayClient.config  
  
 客户端配置文件指定的设置包括：  
  
|设置|XML 元素|描述|允许的值|Required|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|控制器|`<Controller>`|指定控制器的计算机名称。 客户端将尝试通过联系控制器在分布式重播环境中注册。|可以用“`localhost`”或“`.`”指代本地计算机。|否。 默认情况下，客户端会尝试向在本地运行的控制器实例 (“`.`”)（如果存在）注册。|  
|客户端工作目录|`<WorkingDirectory>`|客户端上用于保存调度文件的本地路径。<br /><br /> 此目录中的文件在下一次重播时会被覆盖。|以驱动器号开头的完整目录名称。|否。 如果未指定任何值，则调度文件将与默认客户端配置文件保存在同一位置。 如果指定一个值，而该文件夹在客户端上不存在，则客户端服务不会启动。|  
|客户端结果目录|`<ResultDirectory>`|客户端上用于保存重播活动（针对客户端）的结果跟踪文件的本地路径。<br /><br /> 此目录中的文件在下一次重播时会被覆盖。|以驱动器号开头的完整目录名称。|否。 如果未指定任何值，则结果跟踪文件将与默认客户端配置文件保存在同一位置。 如果指定一个值，而该文件夹在客户端上不存在，则客户端服务不会启动。|  
|日志记录级别|`<LoggingLevel>`|客户端服务的日志记录级别。|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|否。 默认情况下，该值为 `CRITICAL`。|  
  
### <a name="example"></a>示例  
 此示例显示一个客户端配置文件，该文件已经过修改，以指定控制器服务正在名为 `Controller1`的另一台计算机上运行。 `WorkingDirectory` 和 `ResultDirectory` 元素配置为分别使用文件夹 `c:\ClientWorkingDir` 和 `c:\ResultTraceDir`。 日志记录级别已从默认值改为消除 `INFORMATION` 和 `WARNING` 日志条目。  
  
```  
<?xml version='1.0'?>  
<Options>  
    <Controller>Controller1</Controller>  
    <WorkingDirectory>c:\ClientWorkingDir</WorkingDirectory>  
    <ResultDirectory>c:\ResultTraceDir</ResultDirectory>  
    <LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="PreprocessConfig"></a> 预处理配置文件：DReplay.exe.preprocess.config  
 当您使用管理工具启动预处理阶段时，管理工具将从预处理配置文件 `DReplay.exe.preprocess.config` 加载预处理设置。  
  
 使用默认配置文件或使用管理工具的 **-c** 参数来指定修改过的预处理配置文件的位置。 有关使用管理工具的预处理选项的详细信息，请参阅[预处理选项（分布式重播管理工具）](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)。  
  
 默认情况下，预处理配置文件位于安装有管理工具的文件夹中：  
  
 \<管理工具安装路径>\DReplayAdmin\DReplay.exe.preprocess.config  
  
 预处理配置设置在预处理配置文件的 `<PreprocessModifiers>` 元素的子级 XML 元素中指定。 这些设置包括：  
  
|设置|XML 元素|描述|允许的值|Required|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|包括系统会话活动|`<IncSystemSession>`|指示重播期间是否包括捕获过程中的系统会话活动。|`Yes` &#124; `No`|否。 默认情况下，该值为 `No`。|  
|最长空闲时间|`<MaxIdleTime>`|将空闲时间的上限设为某个绝对值（以秒为单位）。|>= -1 的整数。<br /><br /> `-1` 表示原始跟踪文件中的原始值没有变化。<br /><br /> `0` 表示在任意给定时间点有某个活动正在进行。|否。 默认情况下，该值为 `-1`。|  
  
### <a name="example"></a>示例  
 默认预处理配置文件：  
  
```  
<?xml version='1.0'?>  
<Options>  
    <PreprocessModifiers>  
        <IncSystemSession>No</IncSystemSession>  
        <MaxIdleTime>-1</MaxIdleTime>  
    </PreprocessModifiers>  
</Options>  
```  
  
##  <a name="ReplayConfig"></a> 重播配置文件：DReplay.exe.replay.config  
 当您使用管理工具启动事件重播阶段时，管理工具将从重播配置文件 `DReplay.exe.replay.config` 加载重播设置。  
  
 使用默认配置文件或使用管理工具的 **-c** 参数来指定修改过的重播配置文件的位置。 有关使用管理工具的重播选项的详细信息，请参阅[重播选项（分布式重播管理工具）](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)。  
  
 默认情况下，重播配置文件位于安装有管理工具的文件夹中：  
  
 \<管理工具安装路径>\DReplayAdmin\DReplay.exe.replay.config  
  
 重播配置设置在重播配置文件的 `<ReplayOptions>` 和 `<OutputOptions>` 元素的子级 XML 元素中指定。  
  
### <a name="replayoptions-element"></a>\<ReplayOptions > 元素  
 重播配置文件在 `<ReplayOptions>` 元素中指定的设置包括：  
  
|设置|XML 元素|描述|允许的值|Required|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标实例（测试服务器）|`<Server>`|指定要连接的服务器名和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名。|*server_name*[\\*instance_name*]<br /><br /> 不能使用“`localhost`”或“`.`”来表示本地主机。|否，如果已通过使用管理工具的 **-s***target server* 参数和“重播”选项指定服务器名称。|  
|顺序模式|`<SequencingMode>`|指定用于事件计划的模式。|`synchronization` &#124; `stress`|否。 默认情况下，该值为 `stress`。|  
|压力调整粒度|`<StressScaleGranularity>`|指定服务配置文件标识符 (SPID) 上的所有连接在压力模式下是应该一起调整 (SPID) 还是单独调整 (Connection)。|SPID &#124; Connection|是。 默认情况下，该值为 `SPID`。|  
|连接时间刻度|`<ConnectTimeScale>`|用于调整压力模式下的连接时间。|介于 `1` 和 `100`之间的整数。|否。 默认情况下，该值为 `100`。|  
|思考时间刻度|`<ThinkTimeScale>`|用于调整压力模式下的思考时间。|介于 `0` 和 `100`之间的整数。|否。 默认情况下，该值为 `100`。|  
|使用连接池|`<UseConnectionPooling>`|指定是否将在每个分布式重播客户端上启用连接池。|是 &#124; 否|是。 默认情况下，该值为 `Yes`。|  
|Health Monitor 间隔时间|`<HealthmonInterval>`|指示运行 Health Monitor 的频率（以秒为单位）。<br /><br /> 只在同步模式下才使用该值。|>= 1 的整数<br /><br /> （`-1` 为禁用）|否。 默认情况下，该值为 `60`。|  
|查询超时|`<QueryTimeout>`|指定查询超时值（以秒为单位）。 返回第一行后该值才会生效。|>= 1 的整数<br /><br /> （`-1` 为禁用）|否。 默认情况下，该值为 `3600`。|  
|每个客户端的线程数|`<ThreadsPerClient>`|指定要用于每个重播客户端的重播线程数。|介于 `1` 和 `512`之间的整数。|否。 如果未指定，分布式重播将使用值 `255`。|  
  
### <a name="outputoptions-element"></a>\<OutputOptions > 元素  
 重播配置文件在 `<OutputOptions>` 元素中指定的设置包括：  
  
|设置|XML 元素|描述|允许的值|Required|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|记录行计数|`<RecordRowCount>`|指示是否应记录每个结果集的行计数。|`Yes` &#124; `No`|否。 默认情况下，该值为 `Yes`。|  
|记录结果集|`<RecordResultSet>`|指示是否应记录所有结果集的内容。|`Yes` &#124; `No`|否。 默认情况下，该值为 `No`。|  
  
### <a name="example"></a>示例  
 默认重播配置文件：  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server></Server>  
        <SequencingMode>stress</SequencingMode>  
        <ConnectTimeScale></ConnectTimeScale>  
        <ThinkTimeScale></ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  

### <a name="possible-issue-when-running-with-synchronization-sequencing-mode"></a>使用同步序列化模式运行时可能出现的问题
 您可能会遇到一种症状的重播功能出现的"停止"或重播事件速度非常缓慢。 如果在重播的跟踪依赖于数据和/或事件还原的目标数据库中不存在，则会发生这种现象。 
 
例如，在 Service Broker 接收 WAITFOR 语句中使用 waitfor 子句，如捕获工作负荷。 使用同步序列化模式时，批处理是按顺序重播。 如果数据库备份之后发生对源数据库插入，但重播捕获跟踪已启动，在重播过程中发出 WAITFOR 接收可能需要等待 WAITFOR 的整个持续时间。 设置后将停止 WAITFOR 接收要重播的事件。 WAITFOR 完成之前，这可能导致重播数据库目标删除为零的 Batch Requests/sec 性能监视器计数器。 
 
 如果您需要使用同步模式并且想要避免此行为，必须执行以下操作：
 
1.  停止你将使用为重播目标的数据库。

2.  允许所有挂起的活动完成。

3.  备份数据库，并允许备份完成。

4.  启动分布式的重播跟踪捕获和恢复正常工作负荷。 
 
 
## <a name="see-also"></a>另请参阅  
 [管理工具命令行选项（Distributed Replay 实用工具）](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)   
 [SQL Server 分布式重播](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [SQL Server 分布式重播论坛](https://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [使用 Distributed Replay 对 SQL Server 进行负载测试 - 第 2 部分](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [使用 Distributed Replay 对 SQL Server 进行负载测试 – 第 1 部分](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  
