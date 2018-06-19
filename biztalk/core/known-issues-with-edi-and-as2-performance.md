---
title: EDI 和 AS2 效能的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c47294f9-f728-4b6b-abe1-578434eb54df
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e034cf228ee92157c4b29c36660111bb1856c358
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261758"
---
# <a name="known-issues-with-edi-and-as2-performance"></a><span data-ttu-id="3c346-102">EDI 和 AS2 效能的已知問題</span><span class="sxs-lookup"><span data-stu-id="3c346-102">Known Issues with EDI and AS2 Performance</span></span>
<span data-ttu-id="3c346-103">本主題說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 方案在效能方面的已知問題。</span><span class="sxs-lookup"><span data-stu-id="3c346-103">This topic describes known issues with the performance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.</span></span>  
  
## <a name="performance-considerations-for-edi-and-as2-status-reporting"></a><span data-ttu-id="3c346-104">EDI 和 AS2 狀態報告的效能考量</span><span class="sxs-lookup"><span data-stu-id="3c346-104">Performance Considerations for EDI and AS2 Status Reporting</span></span>  
 <span data-ttu-id="3c346-105">當您啟動 EDI 或 AS2 狀態報告時，系統效能可能會受到正在執行狀態報告之訊息的數目所影響。</span><span class="sxs-lookup"><span data-stu-id="3c346-105">When you activate EDI or AS2 status reporting, the performance of your system may be affected by the number of messages that status reporting is performed for.</span></span> <span data-ttu-id="3c346-106">當您選取 EDI 或 AS2 處理的 [儲存報告的交易集/內容] 屬性時，系統效能可能會受到正在執行狀態報告之訊息的大小所影響。</span><span class="sxs-lookup"><span data-stu-id="3c346-106">When you select the "Store transaction set/payload for reporting" property for either EDI or AS2 processing, the performance of your system may be affected by the size of the messages that status reporting is performed for.</span></span>  
  
 <span data-ttu-id="3c346-107">EDI 和 AS2 狀態報告之 BAMPrimaryImport 資料庫中使用的資料表已完成最佳化。</span><span class="sxs-lookup"><span data-stu-id="3c346-107">The tables used in the BAMPrimaryImport database for EDI or AS2 status reporting are optimized.</span></span> <span data-ttu-id="3c346-108">您不需要執行任何最佳化。</span><span class="sxs-lookup"><span data-stu-id="3c346-108">No further optimization is required.</span></span> <span data-ttu-id="3c346-109">不過，您可以變更封存 BAMPrimaryImport 資料庫活動執行個體資料的時間間隔，提高封存 BAM 主要匯入資料庫資料的速率。</span><span class="sxs-lookup"><span data-stu-id="3c346-109">You can, however, increase the rate at which data from the BAM primary import database is archived by changing the time window for archiving activity instance data in the BAMPrimaryImport database.</span></span> <span data-ttu-id="3c346-110">如需詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜封存主要匯入資料庫資料＞。</span><span class="sxs-lookup"><span data-stu-id="3c346-110">For more information, see "Archiving Primary Import Database Data" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="3c346-111">交易集/內容資料是儲存在 BizTalkDTADb 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3c346-111">Transaction set/payload data is stored in the BizTalkDTADb database.</span></span> <span data-ttu-id="3c346-112">如需此資料庫效能的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜瞭解 DTA 追蹤效能行為＞。</span><span class="sxs-lookup"><span data-stu-id="3c346-112">For more information about the performance of this database, see "Understanding DTA Tracking Performance Behavior" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="3c346-113">系統效能也可能會受到系統組態中所啟用之狀態報告的程度所影響。</span><span class="sxs-lookup"><span data-stu-id="3c346-113">Performance of your system may also be affected by the degree of status reporting enabled in the configuration of your system.</span></span> <span data-ttu-id="3c346-114">您可以停用特定類型的狀態報告來提高效能。</span><span class="sxs-lookup"><span data-stu-id="3c346-114">You may be able to improve performance by disabling a specific type of status reporting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c346-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c346-115">See Also</span></span>  
 [<span data-ttu-id="3c346-116">疑難排解 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="3c346-116">Troubleshooting EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)