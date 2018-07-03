---
title: 使用 System Center Operations Manager 2007 監視 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cee8275-bbd0-435f-ac54-07f582190538
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 380af93ccba2671e3ffa3e6377c049eaf23dcd67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995815"
---
# <a name="monitoring-biztalk-server-with-system-center-operations-manager-2007"></a><span data-ttu-id="53446-102">使用 System Center Operations Manager 2007 監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="53446-102">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>
<span data-ttu-id="53446-103">監視您的 BizTalk 應用程式和基礎結構與 Microsoft System Center Operations Manager (Operations Manager) 是慣用的監視方法。</span><span class="sxs-lookup"><span data-stu-id="53446-103">Monitoring your BizTalk applications and infrastructure with Microsoft System Center Operations Manager (Operations Manager) is the preferred monitoring approach.</span></span> <span data-ttu-id="53446-104">Operations Manager 的 Microsoft BizTalk Server 管理組件提供主動式與反應式監視執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="53446-104">The Microsoft BizTalk Server management packs for Operations Manager provide proactive and reactive monitoring of computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="53446-105">這些管理組件提供數十個內建的可自訂的規則，以提供完整且自動化的監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="53446-105">These management packs provide dozens of built-in, customizable rules to allow for comprehensive and automated monitoring of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="53446-106">下列 BizTalk Server 管理組件是適用於 Operations Manager:</span><span class="sxs-lookup"><span data-stu-id="53446-106">The following BizTalk Server management pack is available for use with Operations Manager:</span></span>  
  
- <span data-ttu-id="53446-107">[監視管理組件的 BizTalk Server 2010](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666)。</span><span class="sxs-lookup"><span data-stu-id="53446-107">[BizTalk Server 2010 Monitoring Management Pack](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666).</span></span>  
  
  <span data-ttu-id="53446-108">操作指南的這一節包含的背景資訊、 最佳作法、 檢查清單，且可用來協助實作根據 Operations Manager 的監視策略的程序。</span><span class="sxs-lookup"><span data-stu-id="53446-108">This section of the operations guide includes background information, best practices, checklists, and procedures that you can use to assist in implementing a monitoring strategy based on Operations Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53446-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="53446-109">In This Section</span></span>  
  
-   [<span data-ttu-id="53446-110">使用 Operations Manager 2007 進行監視的最佳做法</span><span class="sxs-lookup"><span data-stu-id="53446-110">Best Practices for Monitoring with Operations Manager 2007</span></span>](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)  
  
-   [<span data-ttu-id="53446-111">使用效能臨界值規則監視節流</span><span class="sxs-lookup"><span data-stu-id="53446-111">Monitoring Throttling Using Performance Threshold Rules</span></span>](../technical-guides/monitoring-throttling-using-performance-threshold-rules.md)  
  
-   [<span data-ttu-id="53446-112">監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="53446-112">Monitoring SQL Servers</span></span>](../technical-guides/monitoring-sql-servers.md)  
  
-   [<span data-ttu-id="53446-113">監視應用程式和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="53446-113">Monitoring Applications and Host Instances</span></span>](../technical-guides/monitoring-applications-and-host-instances.md)