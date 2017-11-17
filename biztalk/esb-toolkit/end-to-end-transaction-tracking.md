---
title: "端對端交易追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebacd2e4-6b5c-4dc4-8361-b5b77042debc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffa49372c54dc526f45e04317e002604ac0914d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-transaction-tracking"></a><span data-ttu-id="76472-102">端對端交易追蹤</span><span class="sxs-lookup"><span data-stu-id="76472-102">End-to-End Transaction Tracking</span></span>
<span data-ttu-id="76472-103">商務可見性與相關的運算子和使用者的能力，來監視流量傳送到執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="76472-103">Business visibility relates to the ability of operators and users to monitor the flow of traffic through the run-time environment.</span></span> <span data-ttu-id="76472-104">企業必須能夠追蹤程序和流經系統在每個步驟，以確保它們播放中造成營收產生其組件的交易。</span><span class="sxs-lookup"><span data-stu-id="76472-104">Enterprises must be able to track the processes and transactions flowing through their systems at each step to ensure that they play their part in contributing to revenue generation.</span></span> <span data-ttu-id="76472-105">AmberPoint SMS 簡化度量單位和 Microsoft BizTalk Server 中的這些訊息的追蹤。</span><span class="sxs-lookup"><span data-stu-id="76472-105">AmberPoint SMS simplifies the measurement and tracking of these messages in Microsoft BizTalk Server.</span></span> <span data-ttu-id="76472-106">系統會允許使用者定義的端對端商務程序流程，而不需要以符合開發人員選擇用來封裝和部署個別的服務元件的方式對齊新管理單位。</span><span class="sxs-lookup"><span data-stu-id="76472-106">The system allows users to define new units of management that align with end-to-end business process flows, instead of being required to conform to the way developers chose to package and deploy individual service components.</span></span> <span data-ttu-id="76472-107">圖 1 顯示定義管理單位的螢幕。</span><span class="sxs-lookup"><span data-stu-id="76472-107">Figure 1 shows the screen for defining management units.</span></span>  
  
 <span data-ttu-id="76472-108">![定義交易的 BizTalk](../esb-toolkit/media/ch9-biztalkdefiningtransaction.gif "Ch9 BizTalkDefiningTransaction")</span><span class="sxs-lookup"><span data-stu-id="76472-108">![BizTalk Defining Transaction](../esb-toolkit/media/ch9-biztalkdefiningtransaction.gif "Ch9-BizTalkDefiningTransaction")</span></span>  
  
 <span data-ttu-id="76472-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="76472-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="76472-110">**新的管理單位中定義的交易**</span><span class="sxs-lookup"><span data-stu-id="76472-110">**Defining a transaction as a new unit of management**</span></span>  
  
 <span data-ttu-id="76472-111">定義之後的交易，使用者可以檢測和追蹤訊息使用的相同工具提供單一服務的可視性，每個交易相關聯。</span><span class="sxs-lookup"><span data-stu-id="76472-111">After defining transactions, users can instrument and track messages associated with each transaction using the same tools that provide visibility into a single service.</span></span> <span data-ttu-id="76472-112">這些工具可以公開效能標準、 監視服務等級協定，針對效能，並產生訊息記錄，如圖 2 所示。</span><span class="sxs-lookup"><span data-stu-id="76472-112">These tools can expose performance metrics, monitor performance against service level agreements, and generate message logs, as shown in Figure 2.</span></span>  
  
 <span data-ttu-id="76472-113">![BizTalk 監控](../esb-toolkit/media/ch9-biztalkmonitoring.gif "Ch9 BizTalkMonitoring")</span><span class="sxs-lookup"><span data-stu-id="76472-113">![BizTalk Monitoring](../esb-toolkit/media/ch9-biztalkmonitoring.gif "Ch9-BizTalkMonitoring")</span></span>  
  
 <span data-ttu-id="76472-114">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="76472-114">**Figure 2**</span></span>  
  
 <span data-ttu-id="76472-115">**監視效能之管線的 「 端對端**</span><span class="sxs-lookup"><span data-stu-id="76472-115">**Monitoring the end-to-end performance of a pipeline**</span></span>  
  
 <span data-ttu-id="76472-116">成功的執行階段控管和系統監控的主要需求是重要的商務事件，例如例外狀況和可能會中斷邏輯的處理商務交易流程的應用程式錯誤偵測。</span><span class="sxs-lookup"><span data-stu-id="76472-116">A major requirement for successful run-time governance and system monitoring is the detection of important business events, such as exceptions and application errors that may disrupt the logical processing of business transaction flows.</span></span> <span data-ttu-id="76472-117">AmberPoint SMS 可讓操作員和使用者來取得深入了解操作和商務事件，並監視這些事件對於依存於服務產生問題的所有元件的影響。</span><span class="sxs-lookup"><span data-stu-id="76472-117">AmberPoint SMS allows operators and users to gain insight into operational and business events and to monitor the impact these events have on all components that depend on the service that generated the problem.</span></span> <span data-ttu-id="76472-118">此外，操作員和使用者可以快速地在疑難排解整個系統來識別問題的根本原因。</span><span class="sxs-lookup"><span data-stu-id="76472-118">In addition, operators and users can quickly troubleshoot the entire system to identify the root-cause of a problem.</span></span>