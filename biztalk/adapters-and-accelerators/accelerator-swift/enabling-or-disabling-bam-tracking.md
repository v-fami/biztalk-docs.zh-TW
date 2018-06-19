---
title: 啟用或停用 BAM 追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, BAM tracking
- BAM tracking
ms.assetid: 07896fab-88a0-4759-8547-16edcd1eebc0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1132c41e9a017e42139d988d1588f79d7d3afaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207390"
---
# <a name="enabling-or-disabling-bam-tracking"></a><span data-ttu-id="cd570-102">啟用或停用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="cd570-102">Enabling or Disabling BAM Tracking</span></span>
<span data-ttu-id="cd570-103">您可以啟用或停用 BAM 追蹤的任何一點，即使訊息修復和新的傳輸處理序在程序中有交易。</span><span class="sxs-lookup"><span data-stu-id="cd570-103">You can enable or disable BAM tracking at any point, even while the Message Repair and New Transmission process has transactions in process.</span></span> <span data-ttu-id="cd570-104">不過，如果您停用 BAM 追蹤的交易中處理程序時，BAM 資料可能不完整，這些交易。</span><span class="sxs-lookup"><span data-stu-id="cd570-104">However, if you disable BAM tracking while transactions are in process, the BAM data may be incomplete for those transactions.</span></span> <span data-ttu-id="cd570-105">如果發生這種情況，歷程記錄資料表仍然會包含所有執行個體的正確資料。</span><span class="sxs-lookup"><span data-stu-id="cd570-105">If this occurs, the history table will still contain accurate data for all instances.</span></span>  
  
 <span data-ttu-id="cd570-106">啟用或停用 BAM 追蹤 A4SWIFT 元件組態程序的相關資訊，請參閱[設定 A4SWIFT 屬性](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cd570-106">For information about enabling or disabling BAM tracking as part of the A4SWIFT component configuration process, see [Setting A4SWIFT Properties](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md).</span></span>  
  
### <a name="to-enable-or-disable-bam-tracking"></a><span data-ttu-id="cd570-107">若要啟用或停用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="cd570-107">To enable or disable BAM Tracking</span></span>  
  
1.  <span data-ttu-id="cd570-108">在設定檔的 Web 用戶端，以滑鼠右鍵按一下**BizTalk Accelerator for SWIFT**在主控台樹狀目錄中，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cd570-108">In the Profile Web Client, right-click **BizTalk Accelerator for SWIFT** in the console tree, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cd570-109">在 [通用屬性] 對話方塊停用 BAM 追蹤取消選取**啟用 BAM 追蹤**，或啟用 BAM 追蹤選取它。</span><span class="sxs-lookup"><span data-stu-id="cd570-109">In the Global Properties dialog box, disable BAM tracking by deselecting **Enable BAM Tracking**, or enable BAM tracking by selecting it.</span></span>  
  
3.  <span data-ttu-id="cd570-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cd570-110">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="cd570-111">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，然後**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="cd570-111">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, and then **Platform Settings**.</span></span> <span data-ttu-id="cd570-112">按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="cd570-112">Click **Host Instances**.</span></span>  
  
5.  <span data-ttu-id="cd570-113">在詳細資料窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="cd570-113">In the details pane, right-click the host instance , and then click **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd570-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd570-114">See Also</span></span>  
 [<span data-ttu-id="cd570-115">設定 A4SWIFT 屬性</span><span class="sxs-lookup"><span data-stu-id="cd570-115">Setting A4SWIFT Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)