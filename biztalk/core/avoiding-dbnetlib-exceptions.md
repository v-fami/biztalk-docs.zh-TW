---
title: "避免 DBNETLIB 例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fbee0cf-d249-4d98-8d16-168ded32f9f1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decd258c5f4c965c79d9821c82671c6997ac9e3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="avoiding-dbnetlib-exceptions"></a><span data-ttu-id="4628c-102">避免 DBNETLIB 例外狀況</span><span class="sxs-lookup"><span data-stu-id="4628c-102">Avoiding DBNETLIB Exceptions</span></span>
<span data-ttu-id="4628c-103">當 BizTalk Server 執行階段無法與 MessageBox 或「管理」資料庫通訊時，會發生 DBNetLib (資料庫網路程式庫) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4628c-103">DBNetLib (Database Network Library) errors occur when the BizTalk Server runtime is unable to communicate with either the MessageBox or Management databases.</span></span> <span data-ttu-id="4628c-104">發生此錯誤時，攔截例外狀況的 BizTalk Server 執行階段執行個體會關閉，然後每分鐘循環查看資料庫是否可以使用。</span><span class="sxs-lookup"><span data-stu-id="4628c-104">When this occurs, the BizTalk Server runtime instance that catches the exception shuts down and then cycles every minute to check to see if the database is available.</span></span>  
  
 <span data-ttu-id="4628c-105">造成 DBNetLib 錯誤最常見的原因是：當其中一個 (可能有多個) MessageBox 資料庫伺服器變得非常忙碌，又嘗試與它通訊時發生逾時，因此造成 DBNetLib 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4628c-105">The most common cause of a DBNetLib error is when one of the (possibly many) MessageBox database servers becomes extremely busy and further attempts to communicate with it result in a timeout, which causes a DBNetLib exception.</span></span>  
  
 <span data-ttu-id="4628c-106">除了 MessageBox 資料庫所在只需非常忙碌的情況下，DBNetLib 錯誤可能在生產環境中裝載多個 MessageBox 資料庫的其中一個 BizTalk 資料庫伺服器變成 I/O （輸入/輸出） 繫結。</span><span class="sxs-lookup"><span data-stu-id="4628c-106">In addition to the case where the MessageBox database is simply very busy, the DBNetLib error can occur in a production environment when BizTalk database servers hosting one of more MessageBox databases become I/O (Input/Output) bound.</span></span>  
  
 <span data-ttu-id="4628c-107">本主題描述可能導致 DBNetLib 錯誤的情況，以及避免這些錯誤的建議。</span><span class="sxs-lookup"><span data-stu-id="4628c-107">This topic describes conditions that can lead to DBNetLib errors and recommendations for avoiding these errors.</span></span>  
  
## <a name="cause-and-resolution-for-the-dbnetlib-error"></a><span data-ttu-id="4628c-108">DBNetLib 錯誤的原因和解決方案</span><span class="sxs-lookup"><span data-stu-id="4628c-108">Cause and Resolution for the DBNetLib error</span></span>  
  
### <a name="symptoms-of-a-dbnetlib-error"></a><span data-ttu-id="4628c-109">DBNetLib 錯誤的徵狀</span><span class="sxs-lookup"><span data-stu-id="4628c-109">Symptoms of a DBNetLib error</span></span>  
 <span data-ttu-id="4628c-110">Microsoft BizTalk Server 主控件執行個體會終止，然後自行重新啟動，並將類似下列的錯誤寫入 BizTalk Server 應用程式記錄檔：</span><span class="sxs-lookup"><span data-stu-id="4628c-110">A Microsoft BizTalk Server host instance terminates and then restarts itself, and errors that are similar to the following are written to the BizTalk Server Application log:</span></span>  
  
```  
Event Type:Warning  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:5410  
Computer:BIZTALKSERVER  
Description:  
An error occurred that requires the BizTalk service to terminate. The most common causes are the following:  
 1) An unexpected out of memory error.  
 OR  
 2) An inability to connect or a loss of connectivity to one of the BizTalk databases.   
 The service will shutdown and auto-restart in 1 minute. If the problematic database remains unavailable, this cycle will repeat.  
  
 Error message: [DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation.  
 Error source:    
  
 BizTalk host name: BizTalkHost  
 Windows service name: BTSSvc$BizTalkHost   
  
---------------------------------------------------------  
Event Type:Error  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:6913  
Computer:BIZTALKSERVER  
Description:  
An attempt to connect to "BizTalkMsgBoxDb" SQL Server database on server "SQLSERVER " failed.  
 Error: "[DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation."  
```  
  
### <a name="biztalk-database-servers-hosting-messagebox-databases-becoming-io-bound"></a><span data-ttu-id="4628c-111">裝載 MessageBox 資料庫的 BizTalk 資料庫伺服器變成 I/O 繫結</span><span class="sxs-lookup"><span data-stu-id="4628c-111">BizTalk database servers hosting MessageBox databases becoming I/O bound</span></span>  
 <span data-ttu-id="4628c-112">BizTalk Server 會直接與裝載 MessageBox 資料庫的資料庫伺服器通訊並作用。</span><span class="sxs-lookup"><span data-stu-id="4628c-112">BizTalk servers communicate and act directly with the database servers hosting the MessageBox databases.</span></span> <span data-ttu-id="4628c-113">若有任何裝載 MessageBox 資料庫的資料庫伺服器過度使用，並進入 I/O 繫結狀況，則資料庫伺服器可能變成反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="4628c-113">If any of the database servers hosting the MessageBox databases get too consumed and gets into an I/O (Input/Output) bound situation, then it might become unresponsive.</span></span> <span data-ttu-id="4628c-114">接著，其中一個 BizTalk Server 可能與這些資料庫伺服器失去連線，會發生 DBNetLib 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4628c-114">One of the BizTalk servers might in turn lose connectivity with one of those database servers, and a DBNetLib error will occur.</span></span>  
  
 <span data-ttu-id="4628c-115">我們的測試顯示，高度使用的資料庫伺服器會在其實體磁碟的「閒置時間百分比」持續下降到 10% 以下時，變成 I/O 繫結。</span><span class="sxs-lookup"><span data-stu-id="4628c-115">Our tests show that a highly consumed database server becomes I/O bound when its physical disk’s "%Idle time" continues to drop and reaches below 10%.</span></span> <span data-ttu-id="4628c-116">若「閒置時間百分比」持續下降到該層級以下，這表示您的資料庫伺服器可能會變成反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="4628c-116">If the “%Idle time” continues to drop below that level, then this is an indication that your database server is likely to become unresponsive.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="4628c-117">原因</span><span class="sxs-lookup"><span data-stu-id="4628c-117">Cause</span></span>  
 <span data-ttu-id="4628c-118">有幾個原因可能造成裝載 MessageBox 資料庫的資料庫伺服器變成 I/O 繫結，下列為其中部分原因：</span><span class="sxs-lookup"><span data-stu-id="4628c-118">There are several reasons that can cause the database servers hosting the MessageBox databases to become I/O bound, some of these are the following:</span></span>  
  
-   <span data-ttu-id="4628c-119">如果裝載 MessageBox 資料庫的資料庫電腦受限於硬體規格不足，例如，記憶體不足、處理器的數目和速度等等</span><span class="sxs-lookup"><span data-stu-id="4628c-119">If the database machine hosting the MessageBox database is bound by low hardware specifications such as: low memory, number and speed of processors etc.</span></span>  
  
-   <span data-ttu-id="4628c-120">若裝載 MessageBox 資料庫之資料庫電腦上的實體磁碟正由其他高度使用的資料庫共用。</span><span class="sxs-lookup"><span data-stu-id="4628c-120">If the physical disk on the database machine hosting a MessageBox database is being shared by other highly consumed databases.</span></span> <span data-ttu-id="4628c-121">在數個資料庫 (包括 MessageBox) 正在同時高度使用的情況下，實體磁碟可能會陷入 I/O 繫結狀況。</span><span class="sxs-lookup"><span data-stu-id="4628c-121">In cases when several databases (including the MessageBox) are being highly consumed at the same time, the physical disk can get into an I/O bound situation.</span></span>  
  
     <span data-ttu-id="4628c-122">這類狀況的範例如下：</span><span class="sxs-lookup"><span data-stu-id="4628c-122">An example of such a situation is the following:</span></span>  
  
     <span data-ttu-id="4628c-123">我們的測試顯示，裝載 BizTalkDTADb 和/或 BAM 資料庫的資料庫伺服器有時會使用高百分比的實體磁碟之「磁碟讀取和寫入次數百分比」。</span><span class="sxs-lookup"><span data-stu-id="4628c-123">Our tests show that the database server hosting the BizTalkDTADb and/or BAM databases sometimes consume high percentages of a physical disk’s %Disk Read and Write Times.</span></span> <span data-ttu-id="4628c-124">當裝載 MessageBox 資料庫的資料庫伺服器磁碟由另一個高度使用的資料庫 (如 BizTalkDTADb 或 BAM) 共用，而這兩個資料庫同時高度使用時，它們可能造成資料庫伺服器實體磁碟變成 I/O 繫結，然後變成反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="4628c-124">When the database server disk that hosts a MessageBox database is being shared by another highly consumed database such as BizTalkDTADb or BAM, and if both databases are highly consumed simultaneously, they might cause the database server physical disk to become I/O bound and then unresponsive.</span></span>  
  
-   <span data-ttu-id="4628c-125">若 BizTalkDTADb 和一或多個 MessageBox 資料庫正在共用資料庫伺服器上的相同實體磁碟，而封存與清除不常執行時，則磁碟可能變成 I/O 繫結。</span><span class="sxs-lookup"><span data-stu-id="4628c-125">If BizTalkDTADb and one or more of the MessageBox databases are sharing the same physical disk on the database server, if archiving and purging is not being run frequently, the disk might become I/O bound.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="4628c-126">解決方案</span><span class="sxs-lookup"><span data-stu-id="4628c-126">Resolution</span></span>  
 <span data-ttu-id="4628c-127">確定裝載 BizTalk MessageBox 的資料庫伺服器不會陷入高度使用和可能反應遲緩的狀況。</span><span class="sxs-lookup"><span data-stu-id="4628c-127">Ensure the database server(s) hosting the BizTalk MessageBox(s) do not get into a situation where they become highly consumed and possibly unresponsive.</span></span>  
  
 <span data-ttu-id="4628c-128">以下列出造成伺服器磁碟變成高度使用的部分主要原因以及如何減輕此問題的建議。</span><span class="sxs-lookup"><span data-stu-id="4628c-128">Some of the primary causes of a server disk becoming highly consumed are listed below along with recommendations on how to mitigate this problem.</span></span>  
  
##### <a name="low-hardware-specs"></a><span data-ttu-id="4628c-129">硬體規格不足</span><span class="sxs-lookup"><span data-stu-id="4628c-129">Low Hardware Specs</span></span>  
 <span data-ttu-id="4628c-130">我們的測試顯示，當伺服器的硬體規格趕不上它所嘗試處理的負載量時，就會開始增加伺服器的使用。</span><span class="sxs-lookup"><span data-stu-id="4628c-130">Our tests show that the server starts getting more consumed when its hardware specifications cannot keep up with the amount of load it’s trying to process.</span></span> <span data-ttu-id="4628c-131">若硬體規格不足，系統很快就會因為發生在資料庫上的活動量而超過負荷。</span><span class="sxs-lookup"><span data-stu-id="4628c-131">With lower hardware specs, the system gets overwhelmed quickly by the amount of activities happening on the databases.</span></span> <span data-ttu-id="4628c-132">這可能造成伺服器的「磁碟讀取和寫入次數百分比」持續增加而不穩定，而且磁碟的「閒置時間百分比」也持續降低到 10% 以下，這可能造成資料庫伺服器變成反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="4628c-132">This might cause the server’s %Disk Read and Write Times to continue increasing without stabilizing, also the disk’s %Idle time to continue to decrease and become lower than 10%, and this might cause your database server to become unresponsive.</span></span>  
  
 <span data-ttu-id="4628c-133">視 BizTalk 部署上的活動量與負載的不同，若您在高負載期間發現資料庫伺服器反應遲緩，應該考慮將資料庫伺服器中的下列部分升級：CPU 數目、記憶體以及連接到 SAN。</span><span class="sxs-lookup"><span data-stu-id="4628c-133">Depending on the amount of activities and load you have on your BizTalk deployment, if you find that you are getting unresponsive database servers during to high loads, you should consider upgrading the following parts in your database servers: number of CPUs, memory, and connecting to a SAN.</span></span> <span data-ttu-id="4628c-134">當然，您應該進行適當的診斷，以找出硬體中哪個部分 (記憶體、CPU 數目等) 是需要升級的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="4628c-134">Of course, you should do the proper diagnosis to figure out which part (memory, number of CPUs etc.) is the bottleneck that needs to be upgraded in your hardware.</span></span>  
  
##### <a name="sharing-one-server-or-disk-for-more-than-one-group-of-biztalk-databases"></a><span data-ttu-id="4628c-135">讓一個以上的 BizTalk 資料庫群組共用一個伺服器或磁碟</span><span class="sxs-lookup"><span data-stu-id="4628c-135">Sharing one server or disk for more than one group of BizTalk databases</span></span>  
 <span data-ttu-id="4628c-136">如先前所提及，MessageBoxes 以外的資料庫 (如 BizTalk 追蹤 (BizTalkDTADb) 資料庫與 BAM 資料庫) 可能高度循環使用伺服器的實體磁碟。</span><span class="sxs-lookup"><span data-stu-id="4628c-136">As mentioned previously, databases other than MessageBoxes, such as the BizTalk Tracking (BizTalkDTADb) database and BAM databases, might consume high cycles on a server’s physical disk.</span></span> <span data-ttu-id="4628c-137">因此，若這些資料庫正好與 MessageBox 資料庫共用相同的實體磁碟，它們就可能阻礙磁碟並使它反應遲緩，這也同樣可能造成 BizTalk Server 與 MessageBox 資料庫失去連線，並因此造成 DBNetLib。</span><span class="sxs-lookup"><span data-stu-id="4628c-137">So, if those databases happen to share the same physical disk with the MessageBox databases, then they might choke the disk and make it unresponsive, which again might cause BizTalk servers to loose connectivity with the MessageBox databases and thus hit DBNetLib.</span></span>  
  
 <span data-ttu-id="4628c-138">強烈建議您將任何預期會高度使用伺服器之實體磁碟的資料庫與 BizTalk MessageBox 分開，如此，它們可以共用不同的實體磁碟 (或是將它們分隔在不同的伺服器)。</span><span class="sxs-lookup"><span data-stu-id="4628c-138">It is highly recommended that you separate any database expected to have high consumption of the server’s physical disk from the BizTalk MessageBox(s), so they share different physical disks (or separate them on different servers).</span></span> <span data-ttu-id="4628c-139">建議您將 BizTalkDTADb 和 BAM 資料庫分隔在 MessageBox 以外的個別磁碟/伺服器上，同時也建議您將每個 MessageBox 資料庫 (在擁有一個以上的 MessageBox 資料庫情形下) 放在其本身的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="4628c-139">It is recommended that you separate the BizTalkDTADb and BAM databases on their own separate drives/servers from the MessageBox(s), and it is also recommended to have each MessageBox database (in the case there is more than one) on it’s own disk.</span></span>  
  
##### <a name="archiving-and-purging"></a><span data-ttu-id="4628c-140">封存與清除</span><span class="sxs-lookup"><span data-stu-id="4628c-140">Archiving and Purging</span></span>  
 <span data-ttu-id="4628c-141">在 BizTalkDTADb 和 MessageBox 資料庫共用相同伺服器的相同磁碟的情況下，您必須定期封存與清除 BizTalkDTADb 資料庫，否則它們將會無限成長。</span><span class="sxs-lookup"><span data-stu-id="4628c-141">In the case when you have BizTalkDTADb and MessageBox databases sharing the same disk on the same server, you must archive and purge your BizTalkDTADb databases regularly, otherwise they will grow indefinitely.</span></span>  
  
 <span data-ttu-id="4628c-142">測試指出，定期封存與清除是較好的作法，不過，若您執行比一般更高的負載，可能要考慮更頻繁地封存與清除。</span><span class="sxs-lookup"><span data-stu-id="4628c-142">Testing indicates that it is good practice to archive and purge periodically, but if you run under higher loads than normal then you might want to consider archiving and purging more frequently.</span></span> <span data-ttu-id="4628c-143">若沒有定期維護 BizTalkDTADb 資料庫的成長，在最後執行這些動作時，可能會花費相當長的時間，並在執行這些動作時使用大部分可用的資料庫伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="4628c-143">If the BizTalkDTADb database growth is not maintained regularly, then when these actions are finally performed they may take considerable time and consume most of the available database server resources while they are running.</span></span>