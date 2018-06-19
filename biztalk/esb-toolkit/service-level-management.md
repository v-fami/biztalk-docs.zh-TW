---
title: 服務等級管理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: add50343-5470-4db3-a029-c827523e2f2c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86b7ba1672660af2a68a5d193729a0a9009173d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294726"
---
# <a name="service-level-management"></a><span data-ttu-id="32056-102">服務層級管理</span><span class="sxs-lookup"><span data-stu-id="32056-102">Service Level Management</span></span>
<span data-ttu-id="32056-103">AmberPoint SMS 服務層級管理員提供特定的效能和可用性的問題，在企業層級 SOA 型系統的可視性。</span><span class="sxs-lookup"><span data-stu-id="32056-103">The AmberPoint SMS Service Level Manager provides visibility into specific performance and availability issues within enterprise-level SOA-based systems.</span></span> <span data-ttu-id="32056-104">它會檢測和追蹤度量的每個 Microsoft BizTalk Server 接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="32056-104">It instruments and tracks the metrics for each Microsoft BizTalk Server receive location and send port.</span></span> <span data-ttu-id="32056-105">這可提供即時健全狀況和狀態指示，除了這些元件進行中的效能特性。</span><span class="sxs-lookup"><span data-stu-id="32056-105">This provides real-time health and status indication, in addition to ongoing performance characterization of these components.</span></span> <span data-ttu-id="32056-106">圖 1 顯示接收位置相關聯的度量的顯示。</span><span class="sxs-lookup"><span data-stu-id="32056-106">Figure 1 shows the display of the metrics associated with a receive location.</span></span>  
  
 <span data-ttu-id="32056-107">![AmberPoint 接收位置](../esb-toolkit/media/ch9-amberpointreceivelocation.gif "Ch9 AmberPointReceiveLocation")</span><span class="sxs-lookup"><span data-stu-id="32056-107">![AmberPoint Receive Location](../esb-toolkit/media/ch9-amberpointreceivelocation.gif "Ch9-AmberPointReceiveLocation")</span></span>  
  
 <span data-ttu-id="32056-108">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="32056-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="32056-109">**接收位置相關聯的度量**</span><span class="sxs-lookup"><span data-stu-id="32056-109">**The metrics associated with a receive location**</span></span>  
  
 <span data-ttu-id="32056-110">AmberPoint 執行階段分析可讓使用者設定的臨界值和系統交叉重大事件的臨界值，包括相容性警告事件、 相容性違規的事件，以及相容性後續返回時傳送警示。</span><span class="sxs-lookup"><span data-stu-id="32056-110">AmberPoint run-time analytics allow users to set thresholds and send alerts when a system crosses a critical event threshold, including compliance warnings events, compliance violations events, and a subsequent return to compliance.</span></span> <span data-ttu-id="32056-111">圖 2 顯示的顯示讓使用者設定服務等級協定及檢視針對此服務等級合約產生的警示。</span><span class="sxs-lookup"><span data-stu-id="32056-111">Figure 2 shows the display where users configure service level agreements and view alerts generated for this service level agreement.</span></span>  
  
 <span data-ttu-id="32056-112">![AmberPoint SLA](../esb-toolkit/media/ch9-amberpointsla.gif "Ch9 AmberPointSLA")</span><span class="sxs-lookup"><span data-stu-id="32056-112">![AmberPoint SLA](../esb-toolkit/media/ch9-amberpointsla.gif "Ch9-AmberPointSLA")</span></span>  
  
 <span data-ttu-id="32056-113">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="32056-113">**Figure 2**</span></span>  
  
 <span data-ttu-id="32056-114">**若要設定服務等級協定及檢視警示螢幕**</span><span class="sxs-lookup"><span data-stu-id="32056-114">**The screens to configure a service level agreement and view alerts**</span></span>  
  
 <span data-ttu-id="32056-115">您可以建立服務層級管理員內的效能目標。</span><span class="sxs-lookup"><span data-stu-id="32056-115">You can establish performance targets within the Service Level Manager.</span></span> <span data-ttu-id="32056-116">軟體然後追蹤個別訊息、 特定的使用者，從訊息中的使用者，以測量效能，針對這些目標群組。</span><span class="sxs-lookup"><span data-stu-id="32056-116">The software then tracks individual messages, messages from a specific user, or messages from groups of users, to measure performance against these targets.</span></span>  
  
 <span data-ttu-id="32056-117">您也可以設定記錄原則，以指示 AmberPoint SMS，以動態方式收集並檢查訊息內容和 BizTalk Server 中，透過傳遞的資料，如圖 3 所示。</span><span class="sxs-lookup"><span data-stu-id="32056-117">You can also configure logging policies that instruct AmberPoint SMS to dynamically collect and inspect message context and data passing through BizTalk Server, as shown in Figure 3.</span></span> <span data-ttu-id="32056-118">您可以接著會遵守業界的特定法規使用這些記錄檔 」 上即時"疑難排解、 技術分析的問題，以及封存。</span><span class="sxs-lookup"><span data-stu-id="32056-118">You can then use these logs for "on-the-fly" troubleshooting, for technical analysis of problems, and for archiving to comply with industry-specific regulations.</span></span>  
  
 <span data-ttu-id="32056-119">![BizTalk 服務訊息](../esb-toolkit/media/ch9-biztalkservicemessages.jpg "Ch9 BizTalkServiceMessages")</span><span class="sxs-lookup"><span data-stu-id="32056-119">![BizTalk Service Messages](../esb-toolkit/media/ch9-biztalkservicemessages.jpg "Ch9-BizTalkServiceMessages")</span></span>  
  
 <span data-ttu-id="32056-120">**圖 3**</span><span class="sxs-lookup"><span data-stu-id="32056-120">**Figure 3**</span></span>  
  
 <span data-ttu-id="32056-121">**記錄檔中的 BizTalk Server 服務的訊息**</span><span class="sxs-lookup"><span data-stu-id="32056-121">**The log file for BizTalk Server service messages**</span></span>