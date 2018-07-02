---
title: 監視磁碟空間使用量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ac68022-a9c5-4eb9-8854-cd1ee849282b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25035d50c6e69fcf74e1cf75e8f073b19cc0b47f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986927"
---
# <a name="monitoring-disk-space-usage"></a><span data-ttu-id="be285-102">監視磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="be285-102">Monitoring Disk Space Usage</span></span>
<span data-ttu-id="be285-103">作業整備狀態的監視程序的一部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，監視磁碟空間使用量，如下所示：</span><span class="sxs-lookup"><span data-stu-id="be285-103">As part of the monitoring process for operational readiness of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], monitor the disk space usage as follows:</span></span>  

- <span data-ttu-id="be285-104">**決定磁碟所需的空間。**</span><span class="sxs-lookup"><span data-stu-id="be285-104">**Determine the disk space required.**</span></span>  

   <span data-ttu-id="be285-105">當使用檔案或 MSMQ 傳送 / 接收位置時，請確定沒有足夠的磁碟空間可容納的中斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或接收的系統。</span><span class="sxs-lookup"><span data-stu-id="be285-105">When using File or MSMQ send / receive locations, ensure that there is ample disk space available to accommodate outages of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or of the receiving systems.</span></span> <span data-ttu-id="be285-106">例如，如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 SAN 上的寫入檔案共用，而且接收端系統已關閉兩天內，判斷是否有足夠的磁碟空間，以允許檔案排入佇列。</span><span class="sxs-lookup"><span data-stu-id="be285-106">For example, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is writing files to a share on a SAN and the receiving system is down for two days, determine whether there is enough disk space to allow the files to queue up.</span></span>  

- <span data-ttu-id="be285-107">**定期清除 BizTalk Server 的備份檔案的目錄。**</span><span class="sxs-lookup"><span data-stu-id="be285-107">**Clean up the BizTalk Server backup files directory periodically.**</span></span>  

   <span data-ttu-id="be285-108">您可以執行使用指令碼從 SQL Server Agent 作業呼叫此清除工作。</span><span class="sxs-lookup"><span data-stu-id="be285-108">You can perform this cleanup using a script called from a SQL Server Agent job.</span></span>  

- <span data-ttu-id="be285-109">**定期清除 BizTalk 追蹤資料庫封存的檔案目錄。**</span><span class="sxs-lookup"><span data-stu-id="be285-109">**Clean up the BizTalk Tracking database archive files directory periodically.**</span></span>  

- <span data-ttu-id="be285-110">**請確定沒有足夠的磁碟空間可容納更大的 BizTalk Server 資料庫 (.mdf) 和交易記錄 (.ldf) 檔案最大資源資料流中的時間。**</span><span class="sxs-lookup"><span data-stu-id="be285-110">**Ensure that there is sufficient disk space available to accommodate larger BizTalk Server database (.mdf) and transaction log (.ldf) files during times of peak data flow.**</span></span>
