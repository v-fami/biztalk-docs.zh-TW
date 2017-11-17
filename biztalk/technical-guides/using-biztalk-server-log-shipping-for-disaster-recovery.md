---
title: "使用 BizTalk Server 記錄傳送災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d65015c-de53-4590-b644-5c2f66f763db
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16f2cf9e1d8b717ff42536ef9c0dba79132b9663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-log-shipping-for-disaster-recovery"></a><span data-ttu-id="ea092-102">使用 BizTalk Server 記錄傳送災害復原</span><span class="sxs-lookup"><span data-stu-id="ea092-102">Using BizTalk Server Log Shipping for Disaster Recovery</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ea092-103">實作資料庫待命的功能，透過使用資料庫記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="ea092-103"> implements database standby capabilities through the use of database log shipping.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ea092-104">記錄傳送會自動備份和還原的資料庫和交易記錄檔，允許繼續處理的實際執行資料庫伺服器失敗，資料庫的待命伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea092-104"> log shipping automates the backup and restore of database and transaction log files, allowing a standby server to resume database processing in the event that the production database server fails.</span></span>  
  
## <a name="how-log-shipping-works"></a><span data-ttu-id="ea092-105">如何記錄檔傳送運作</span><span class="sxs-lookup"><span data-stu-id="ea092-105">How Log Shipping Works</span></span>  
 <span data-ttu-id="ea092-106">[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所使用的代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送同步處理在生產環境中使用的來源伺服器與目的地伺服器作為備用，以每隔 15 分鐘預設使用 （每個 「 備份 BizTalk Server 」 工作執行的時間） 之間的資料。</span><span class="sxs-lookup"><span data-stu-id="ea092-106">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for log shipping synchronize data between the source server used in production and the destination server used as a standby every 15 minutes by default (every time that the Backup BizTalk Server job runs).</span></span>  
  
## <a name="using-log-shipping-for-disaster-recovery"></a><span data-ttu-id="ea092-107">使用記錄傳送災害復原</span><span class="sxs-lookup"><span data-stu-id="ea092-107">Using Log Shipping for Disaster Recovery</span></span>  
 <span data-ttu-id="ea092-108">執行下列動作時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送災害復原：</span><span class="sxs-lookup"><span data-stu-id="ea092-108">Do the following when using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping for disaster recovery:</span></span>  
  
-   <span data-ttu-id="ea092-109">遵循本主題中的步驟[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)以提高可用性生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原。</span><span class="sxs-lookup"><span data-stu-id="ea092-109">Follow the steps in the topic [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) to increase availability of a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment using disaster recovery.</span></span>  
  
-   <span data-ttu-id="ea092-110">請確認嚴重損壞修復伺服器有能力處理生產負載。</span><span class="sxs-lookup"><span data-stu-id="ea092-110">Verify that the disaster recovery servers have the capacity to handle production load.</span></span>  
  
     <span data-ttu-id="ea092-111">確定待命伺服器具有相同或類似可用的資源 （CPU/記憶體/磁碟） 做為實際執行伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea092-111">Ensure that the standby servers have the same or similar resources available (CPU/memory/disk) as the production servers.</span></span>  
  
-   <span data-ttu-id="ea092-112">請確定您的災害復原常式的細節會完善記載。</span><span class="sxs-lookup"><span data-stu-id="ea092-112">Ensure that the specifics of your disaster recovery routine are well documented.</span></span>  
  
     <span data-ttu-id="ea092-113">您的嚴重損壞修復的準備和實作詳細資料中的每個步驟的文件。</span><span class="sxs-lookup"><span data-stu-id="ea092-113">Document every step of your disaster recovery preparation and implementation in detail.</span></span> <span data-ttu-id="ea092-114">嚴重損壞很少攻擊時很方便，我們假設負責實作嚴重損壞修復程序的合作對象，開始其第一天的工作，而且會進行這個第一次。</span><span class="sxs-lookup"><span data-stu-id="ea092-114">Disaster seldom strikes when it is convenient so assume that the parties responsible for implementing the disaster recovery procedure are starting their first day of work and will be doing this for the first time.</span></span>  
  
-   <span data-ttu-id="ea092-115">一般測試的作法是容錯移轉至災害復原站台的一部分，尤其是以新的 BizTalk 應用程式會放在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="ea092-115">As part of regular testing, practice failover to the disaster recovery site, especially as new BizTalk applications are put in production.</span></span>  
  
     <span data-ttu-id="ea092-116">執行測試時的一般測試和維護，以確保它可以執行順暢的容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="ea092-116">Perform failover testing as a part of regular testing and maintenance to ensure that it can be performed smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea092-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea092-117">See Also</span></span>  
 [<span data-ttu-id="ea092-118">嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="ea092-118">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)