---
title: 還原程序中的間距 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 616c4f36-8ed6-4b99-b97a-5635627dfc17
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7d3ccadd950f5a955430b982c1a6f79a262864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298094"
---
# <a name="gaps-in-the-restore-process"></a><span data-ttu-id="6e7b1-102">還原程序中的間距</span><span class="sxs-lookup"><span data-stu-id="6e7b1-102">Gaps in the Restore Process</span></span>
<span data-ttu-id="6e7b1-103">Master.dbo.bts_LogShippingHistory 資料表中的記錄時，您可能會注意到還原集合中的間距。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-103">When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may observe gaps in restored sets.</span></span> <span data-ttu-id="6e7b1-104">這可能有數種原因。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-104">This can occur for several reasons.</span></span> <span data-ttu-id="6e7b1-105">不過，即使在發生間斷時，才可以還原的目的系統穩定性。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-105">However, the stability of the destination system can be restored even when gaps have occurred.</span></span> <span data-ttu-id="6e7b1-106">間隔必須後面集，才能修復目的地環境的完整備份的還原。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-106">A gap must be followed by a restore of a full backup set to repair the destination environment.</span></span> <span data-ttu-id="6e7b1-107">如果間斷之後沒有接著還原的完整備份組，目的地環境可能會不穩定且無法還原處於一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-107">If a gap is not followed by a full backup set restore, the destination environment is not stable and cannot be restored in a consistent state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e7b1-108">還原完整備份的目的只是要初步建立資料庫，並修復記錄檔歷程記錄備份鏈結中的問題。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-108">Full backups are only restored to initially create the database and to repair problems in the log history backup chain.</span></span> <span data-ttu-id="6e7b1-109">只要還原，不會發生這個問題，完整備份組未還原，因為它們不會參與記錄備份鏈結。</span><span class="sxs-lookup"><span data-stu-id="6e7b1-109">As long as a problem does not occur with a restore, full backup sets are not restored, because they do not participate in the log backup chain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7b1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e7b1-110">See Also</span></span>  
 [<span data-ttu-id="6e7b1-111">疑難排解記錄傳送</span><span class="sxs-lookup"><span data-stu-id="6e7b1-111">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)