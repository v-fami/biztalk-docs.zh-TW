---
title: "如何避免磁碟 Contention1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b4f8e10-16b0-45f9-8787-da16266da980
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 702665046dbaee77412675e4be0edc602dd9e7e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-disk-contention"></a><span data-ttu-id="5308f-102">如何避免磁碟爭用</span><span class="sxs-lookup"><span data-stu-id="5308f-102">How to Avoid Disk Contention</span></span>
<span data-ttu-id="5308f-103">BizTalk Server 設計為一個持續性的系統，因此在高輸送量的情況下，MessageBox 可能會遇到嚴重的爭用情況。</span><span class="sxs-lookup"><span data-stu-id="5308f-103">BizTalk Server is designed as a persistent system whereby, for high throughput scenarios, the MessageBox can experience severe contention.</span></span> <span data-ttu-id="5308f-104">這個爭用情況可能會因緩慢的磁碟而加重。</span><span class="sxs-lookup"><span data-stu-id="5308f-104">This contention can be aggravated by slow disks.</span></span> <span data-ttu-id="5308f-105">如果磁碟緩慢 (磁碟閒置時間的百分比很低)，這可能會造成 SQL 鎖定更久 (高鎖定等候時間及高鎖定逾時)，使得 MessageBox 表格 (多工緩衝處理和應用程式佇列) 變大、讓資料庫膨脹，而節流最後會讓整體可持續的輸送量變低。</span><span class="sxs-lookup"><span data-stu-id="5308f-105">If the disks are slow (low % Disk Idle Time), this can cause SQL to hold onto locks longer (high Lock Wait Time and high Lock Timeouts) which can cause the MessageBox tables (Spool and Application Queues) to grow, causing database bloat and throttling ultimately resulting in lower overall sustainable throughput.</span></span>  
  
 <span data-ttu-id="5308f-106">若要避免磁碟爭用情況，建議您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5308f-106">To avoid disk contention, it is recommended that you do the following:</span></span>  
  
-   <span data-ttu-id="5308f-107">使用高速 (多磁針) 磁碟。</span><span class="sxs-lookup"><span data-stu-id="5308f-107">Use of high speed (multiple spindles) disks.</span></span>  
  
-   <span data-ttu-id="5308f-108">可能的話，在高速 SAN 上部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="5308f-108">If possible, deploy the databases on a high speed SAN.</span></span> <span data-ttu-id="5308f-109">如果有多個資料庫共用相同的磁碟，建議您在不同的專用磁碟上設定這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="5308f-109">If multiple databases are sharing the same disks it is recommended to configure them on separate dedicated disks.</span></span> <span data-ttu-id="5308f-110">此外，也建議您將 MessageBox 資料庫的 MDF 和 LDF 檔案分開放到不同的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="5308f-110">In addition it is recommended to separate the MDF and LDF files for the MessageBox database onto separate disks.</span></span>  
  
-   <span data-ttu-id="5308f-111">如果 SQL 非常需要 CPU，請考慮將 MessageBox 資料庫分開放到與追蹤資料庫不同的專用伺服器上。</span><span class="sxs-lookup"><span data-stu-id="5308f-111">If SQL is starved for CPU, consider separating the MessageBox database onto a dedicated server that is separate from the Tracking databases.</span></span>  
  
-   <span data-ttu-id="5308f-112">設定好 MessageBox 資料庫專用的伺服器之後，請考慮升級 CPU 及/或新增更多的 CPU。</span><span class="sxs-lookup"><span data-stu-id="5308f-112">After setting up a dedicated server for the MessageBox database, consider scaling up by upgrading the CPU’s and/or adding more CPU’s.</span></span> <span data-ttu-id="5308f-113">監視 SQL Server 的本機磁碟機，因為 MSDTC 記錄會儲存在本機磁碟機 (C:\WINDOWS\system32\Msdtc)。</span><span class="sxs-lookup"><span data-stu-id="5308f-113">Monitor the local drive on the SQL-Server as the MSDTC logs are saved on the local drive (C:\WINDOWS\system32\Msdtc).</span></span>  
  
-   <span data-ttu-id="5308f-114">如果因為 PageFile 或 MSDTC 記錄的原因，而在本機磁碟機上造成爭用，請嘗試將 PageFile 及/或 MSDTC 記錄移到另一個磁碟機。</span><span class="sxs-lookup"><span data-stu-id="5308f-114">If there is contention on the local drive due to the PageFile or MSDTC log, try moving the PageFile and/or the MSDTC log to a separate drive.</span></span>