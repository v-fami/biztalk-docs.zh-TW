---
title: 監控 BizTalk Server 記錄傳送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fae4ff40-7d86-4e9b-b1cc-4f00486ae4b9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eacec106823afc8203e7cce9679cb27cd29d0b78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298566"
---
# <a name="monitoring-biztalk-server-log-shipping"></a><span data-ttu-id="db634-102">監控 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="db634-102">Monitoring BizTalk Server Log Shipping</span></span>
<span data-ttu-id="db634-103">若要判斷上次成功的備份組的 BizTalk Server 資料庫和還原的記錄檔，請檢視 Master.dbo.bts_LogShippingHistory 資料表，在目的地上的內容[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="db634-103">To determine the last successful backup set of BizTalk Server databases and logs that have been restored, review the contents of the Master.dbo.bts_LogShippingHistory table on the destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span> <span data-ttu-id="db634-104">此資料表會擴展由 「 BizTalk Server 記錄傳送取得備份歷程記錄 」 工作，且更新所還原作業。</span><span class="sxs-lookup"><span data-stu-id="db634-104">This table is populated by the BizTalk Server Log Shipping Get Backup History job and is updated by the restore job.</span></span> <span data-ttu-id="db634-105">已成功還原備份，還原的資料行設定為 1 的值，並將 RestoredDateTime 設定為目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="db634-105">When a backup is successfully restored, the Restored column is set to a value of 1 and the RestoredDateTime is set to the current date and time.</span></span>  
  
 <span data-ttu-id="db634-106">當所有資料庫還原至伺服器特定備份組 Master.dbo.bts_LogShippingHistory 資料表中列出從已成功還原時，備份集識別碼會寫入 Master.dbo.bts_LogShippingLastRestoreSet 資料表中。</span><span class="sxs-lookup"><span data-stu-id="db634-106">When all of the databases restored to the server from a particular backup set listed in the Master.dbo.bts_LogShippingHistory table have been successfully restored, the backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table.</span></span> <span data-ttu-id="db634-107">此資料表會儲存設定還原的最後一個，並判斷哪個備份組的記錄檔要還原至災害復原事件發生之後讓目的地 BizTalk 群組上線時很有用。</span><span class="sxs-lookup"><span data-stu-id="db634-107">This table stores the last set restored and is useful for determining what backup set of logs need to be restored to bring the destination BizTalk group online after the occurrence of a disaster recovery event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db634-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db634-108">See Also</span></span>  
 [<span data-ttu-id="db634-109">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="db634-109">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)