---
title: "檢視的記錄備份還原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring, history
- backing up, history
ms.assetid: 8852befa-b8e7-469d-b014-75c881907442
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa5a7fbe2b0e731920880570b0555402ba162c7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-the-history-of-restored-backups"></a><span data-ttu-id="a6ba1-102">檢視所還原備份的歷程記錄</span><span class="sxs-lookup"><span data-stu-id="a6ba1-102">Viewing the History of Restored Backups</span></span>
<span data-ttu-id="a6ba1-103">若要判斷上一個已還原的成功備份集，請檢視 Master.dbo.bts_LogShippingHistory 資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-103">To determine the last successful backup set restored, review the contents of the Master.dbo.bts_LogShippingHistory table.</span></span> <span data-ttu-id="a6ba1-104">這個資料表是由「取得備份歷程記錄」工作填入，並且由「還原資料庫」工作更新。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-104">This table is populated by the Get Backup History job and updated by the Restore Databases job.</span></span> <span data-ttu-id="a6ba1-105">成功還原備份時，會將 [已還原] 欄設定為 1，並將 RestoredDateTime 設定為目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-105">When a backup is successfully restored, the Restored column is set to 1 and the RestoredDateTime is set to the current date and time.</span></span>  
  
 <span data-ttu-id="a6ba1-106">成功還原所有由特定備份集還原到伺服器的資料庫之後，該備份集識別碼會寫入 Master.dbo.bts_LogShippingLastRestoreSet 資料表。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-106">When all of the databases being restored to the server from a particular backup set have been successfully restored, that backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table.</span></span>  
  
## <a name="gaps-in-the-restore-process"></a><span data-ttu-id="a6ba1-107">還原程序中的間斷</span><span class="sxs-lookup"><span data-stu-id="a6ba1-107">Gaps in the restore process</span></span>  
 <span data-ttu-id="a6ba1-108">檢視 Master.dbo.bts_LogShippingHistory 資料表中的記錄時，您可能會在還原的備份集中發現一些間斷。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-108">When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may find gaps in the sets restored.</span></span> <span data-ttu-id="a6ba1-109">這可能有數種原因。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-109">This can occur for several reasons.</span></span> <span data-ttu-id="a6ba1-110">不過，即使在發生間斷時，您仍然可以回復目的地系統 (即備份電腦) 的穩定性。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-110">However, you can still recover the stability of your destination system (which are your backup computers), even when gaps have occurred.</span></span> <span data-ttu-id="a6ba1-111">間斷之後必須緊接著還原完整備份集，才能修復目的地系統。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-111">A gap must be followed by a restore of a full backup set to repair the destination system.</span></span> <span data-ttu-id="a6ba1-112">如果間斷之後沒有接著還原完整備份集，則目的地環境就會不穩定。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-112">If a gap is not followed by a full backup set restore, the destination environment is not stable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6ba1-113">還原完整備份的目的只是要初步建立資料庫，並修復記錄檔歷程記錄備份鏈結中的問題。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-113">Full backups are only restored to initially create the database and to repair problems in the log history backup chain.</span></span> <span data-ttu-id="a6ba1-114">不過，多數情況下均無法還原完整備份集，因為這些備份集並非記錄備份鏈結中的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6ba1-114">In most cases full backup sets are not restored, as they are not part of the log backup chain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ba1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6ba1-115">See Also</span></span>  
 [<span data-ttu-id="a6ba1-116">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="a6ba1-116">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)