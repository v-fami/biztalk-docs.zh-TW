---
title: "監控 BizTalk Server 與 System Center Operations Manager 2007 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee8275-bbd0-435f-ac54-07f582190538
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdaa0f0639bc640e87ff59e3cee0c229319de4ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-biztalk-server-with-system-center-operations-manager-2007"></a><span data-ttu-id="1d3fe-102">監控 BizTalk Server 與 System Center Operations Manager 2007</span><span class="sxs-lookup"><span data-stu-id="1d3fe-102">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>
<span data-ttu-id="1d3fe-103">監視您的 BizTalk 應用程式和基礎結構與 Microsoft System Center Operations Manager (Operations Manager) 是慣用的監視方法。</span><span class="sxs-lookup"><span data-stu-id="1d3fe-103">Monitoring your BizTalk applications and infrastructure with Microsoft System Center Operations Manager (Operations Manager) is the preferred monitoring approach.</span></span> <span data-ttu-id="1d3fe-104">Operations Manager 的 Microsoft BizTalk Server 管理組件提供主動式與反應式監視執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d3fe-104">The Microsoft BizTalk Server management packs for Operations Manager provide proactive and reactive monitoring of computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1d3fe-105">這些管理組件提供數十個內建的自訂規則以允許完整且自動化的監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d3fe-105">These management packs provide dozens of built-in, customizable rules to allow for comprehensive and automated monitoring of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1d3fe-106">下列 BizTalk Server 管理組件是可使用在 Operations Manager:</span><span class="sxs-lookup"><span data-stu-id="1d3fe-106">The following BizTalk Server management pack is available for use with Operations Manager:</span></span>  
  
-   <span data-ttu-id="1d3fe-107">[監視管理組件的 BizTalk Server 2010](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666)。</span><span class="sxs-lookup"><span data-stu-id="1d3fe-107">[BizTalk Server 2010 Monitoring Management Pack](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666).</span></span>  
  
 <span data-ttu-id="1d3fe-108">操作指南的這個章節包括背景資訊、 最佳做法、 檢查清單和您可以使用以協助實作根據 Operations Manager 監視策略的程序。</span><span class="sxs-lookup"><span data-stu-id="1d3fe-108">This section of the operations guide includes background information, best practices, checklists, and procedures that you can use to assist in implementing a monitoring strategy based on Operations Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d3fe-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="1d3fe-109">In This Section</span></span>  
  
-   [<span data-ttu-id="1d3fe-110">使用 Operations Manager 2007 進行監視的最佳做法</span><span class="sxs-lookup"><span data-stu-id="1d3fe-110">Best Practices for Monitoring with Operations Manager 2007</span></span>](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)  
  
-   [<span data-ttu-id="1d3fe-111">使用效能臨界值規則監視節流</span><span class="sxs-lookup"><span data-stu-id="1d3fe-111">Monitoring Throttling Using Performance Threshold Rules</span></span>](../technical-guides/monitoring-throttling-using-performance-threshold-rules.md)  
  
-   [<span data-ttu-id="1d3fe-112">監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d3fe-112">Monitoring SQL Servers</span></span>](../technical-guides/monitoring-sql-servers.md)  
  
-   [<span data-ttu-id="1d3fe-113">監視應用程式和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="1d3fe-113">Monitoring Applications and Host Instances</span></span>](../technical-guides/monitoring-applications-and-host-instances.md)