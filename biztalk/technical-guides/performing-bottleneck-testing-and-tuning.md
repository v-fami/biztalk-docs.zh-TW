---
title: 執行瓶頸測試與微調 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95d41d95-3a76-4eb0-b07d-14c6b6dccdaa
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 468f7a3a35922c6348369050593cbb56b56457d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018591"
---
# <a name="performing-bottleneck-testing-and-tuning"></a><span data-ttu-id="8bb8d-102">執行瓶頸測試與微調</span><span class="sxs-lookup"><span data-stu-id="8bb8d-102">Performing Bottleneck Testing and Tuning</span></span>
<span data-ttu-id="8bb8d-103">您應該先完成效能測試以判斷系統中的瓶頸，並據以調整系統。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-103">You should complete performance testing to determine bottlenecks in the system and to tune the system accordingly.</span></span>  
  
## <a name="testing-a-subsystem"></a><span data-ttu-id="8bb8d-104">測試一個子系統</span><span class="sxs-lookup"><span data-stu-id="8bb8d-104">Testing a Subsystem</span></span>  
 <span data-ttu-id="8bb8d-105">找出系統瓶頸的最佳作法是整個系統，子集上執行效能測試，例如：</span><span class="sxs-lookup"><span data-stu-id="8bb8d-105">A best practice for identifying system bottlenecks is to run performance tests on subsets of the entire system, for example:</span></span>  
  
- <span data-ttu-id="8bb8d-106">建立傳送或接收訊息的外部系統的基準效能參數[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-106">Establish baseline performance parameters for external systems that send messages to or receive message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="8bb8d-107">登錄協調流程，但不是啟動它們。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-107">Enlist orchestrations, but do not start them.</span></span> <span data-ttu-id="8bb8d-108">卸除訊息的輸入的佇列/檔案位置，讓傳入接收配接器清空佇列/檔案位置，並將訊息發佈至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-108">Drop messages into the inbound queues/file locations and let the inbound receive adapters drain the queue/file locations and publish messages into the MessageBox database.</span></span> <span data-ttu-id="8bb8d-109">這可讓您找出您的接收連接埠，以判斷其最大持續性的輸入的速率。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-109">This allows you to isolate your receive ports to determine their maximum sustained input rate.</span></span>  
  
- <span data-ttu-id="8bb8d-110">訊息會提取至 MessageBox 資料庫之後再, 停止接收配接器、 啟用的協調流程處理程序和/或傳送配接器，然後測量的速率在哪一個協調流程和/或傳送配接器處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-110">Once the messages are pulled into the MessageBox database, stop the receive adapters, enable the orchestration processes and/or send adapters, and then measure the rate at which orchestrations and/or send adapters are processing messages.</span></span>  
  
## <a name="testing-the-end-to-end-system"></a><span data-ttu-id="8bb8d-111">測試端對端系統</span><span class="sxs-lookup"><span data-stu-id="8bb8d-111">Testing the End-to-End System</span></span>  
 <span data-ttu-id="8bb8d-112">上一節所述的輸入和輸出速率測試是有效的方式，來隔離應用程式子系統的效能，雖然它不會說明端對端的效能。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-112">Testing of input and output rates as described in preceding section is an effective way to isolate performance of the application subsystem, although it does not describe end-to-end performance.</span></span> <span data-ttu-id="8bb8d-113">您也應該測試端對端效能，因為無法識別有些瓶頸，直到開始爭用相同的共用資源 （例如，MessageBox 資料庫） 的多個資源。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-113">You should also test end-to-end performance because some bottlenecks cannot be identified until multiple resources begin to contend for the same shared resource (for example, the MessageBox database).</span></span>  
  
 <span data-ttu-id="8bb8d-114">若要產生負載與針對[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請考慮使用 Microsoft BizTalk LoadGen 2007 工具。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-114">To generate load against a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, consider using the Microsoft BizTalk LoadGen 2007 tool.</span></span> <span data-ttu-id="8bb8d-115">下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-115">Download [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).</span></span>  
  
 <span data-ttu-id="8bb8d-116">產生並分析效能報告[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請考慮使用效能分析的記錄檔 (PAL) 工具。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-116">To generate and analyze a performance report for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, consider using the Performance Analysis of Logs (PAL) tool.</span></span> <span data-ttu-id="8bb8d-117">如需有關 PAL tool 的詳細資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-117">For more information about the PAL tool, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).</span></span>  
  
## <a name="what-developers-operators-and-administrators-should-know"></a><span data-ttu-id="8bb8d-118">應該要知道哪些開發人員、 運算子和系統管理員</span><span class="sxs-lookup"><span data-stu-id="8bb8d-118">What Developers, Operators, and Administrators Should Know</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8bb8d-119"> 開發人員應該十分熟悉上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能特性和調整。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-119"> developers should be well versed on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance characteristics and tuning.</span></span> <span data-ttu-id="8bb8d-120">操作員和系統管理員應該了解 MessageBox 資料庫向外延展的層面，SAN 微調，網路微調和調整 SQL Server 資料庫 (例如，請參閱[SQL Server 設定，不應變更](../technical-guides/sql-server-settings-that-should-not-be-changed.md))。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-120">Operators and administrators should be knowledgeable about MessageBox database scale-out aspects, SAN tuning, network tuning, and SQL Server database tuning (for example, see [SQL Server Settings That Should Not Be Changed](../technical-guides/sql-server-settings-that-should-not-be-changed.md)).</span></span> <span data-ttu-id="8bb8d-121">開發人員、 運算子和系統管理員應該了解如何調整[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]高輸送量和低延遲。</span><span class="sxs-lookup"><span data-stu-id="8bb8d-121">Developers, operators, and administrators should be aware of how to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for high-throughput and low-latency.</span></span>