---
title: "執行可用性測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b543dd-ba85-40da-8c6f-485eddb59158
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6f0d9b1cb7b38ab8a1173ee227a8202812048f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performing-availability-testing"></a><span data-ttu-id="f75f2-102">執行可用性測試</span><span class="sxs-lookup"><span data-stu-id="f75f2-102">Performing Availability Testing</span></span>
<span data-ttu-id="f75f2-103">您應該測試系統，以確認它能夠從各種層級失敗時，範圍介於小規模失敗 （例如網路卡失敗） 至實際執行伺服器遺失復原的嚴重損壞修復。</span><span class="sxs-lookup"><span data-stu-id="f75f2-103">You should test your system for disaster recovery to verify its ability to recover from various levels of failure, ranging from small-scale failures (such as a network card failure) to the loss of a production server.</span></span> <span data-ttu-id="f75f2-104">您損毀修復測試應該包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f75f2-104">Your disaster recovery testing should include the following steps:</span></span>  
  
-   <span data-ttu-id="f75f2-105">**測試個別硬體元件失敗。**</span><span class="sxs-lookup"><span data-stu-id="f75f2-105">**Test individual hardware component failure.**</span></span>  
  
     <span data-ttu-id="f75f2-106">您應該測試系統能夠從個別的硬體元件失敗，例如網路或磁碟中復原。</span><span class="sxs-lookup"><span data-stu-id="f75f2-106">You should test the ability of the system to recover from an individual hardware component failure, such as a network or disk.</span></span>  
  
-   <span data-ttu-id="f75f2-107">**測試單一 BizTalk server 失敗。**</span><span class="sxs-lookup"><span data-stu-id="f75f2-107">**Test single BizTalk server failure.**</span></span>  
  
     <span data-ttu-id="f75f2-108">在大部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]生產環境中，主機處理分散多部電腦執行間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]單一的 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="f75f2-108">In most [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environments, host processing is spread out among multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a single BizTalk group.</span></span> <span data-ttu-id="f75f2-109">什麼是 BizTalk 群組能夠繼續在事件處理的主機群組中伺服器的其中一個失敗？</span><span class="sxs-lookup"><span data-stu-id="f75f2-109">What is the ability of the BizTalk group to continue host processing in the event one of the servers in the group fails?</span></span>  
  
-   <span data-ttu-id="f75f2-110">**測試叢集節點容錯移轉。**</span><span class="sxs-lookup"><span data-stu-id="f75f2-110">**Test cluster node failover.**</span></span>  
  
     <span data-ttu-id="f75f2-111">如果使用 Windows 叢集提供高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或 BizTalk 主控件，您應該確認叢集節點容錯移轉功能。</span><span class="sxs-lookup"><span data-stu-id="f75f2-111">If Windows Clustering is used to provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases or BizTalk Hosts, you should verify cluster node failover functionality.</span></span> <span data-ttu-id="f75f2-112">如需有關使用 Windows 叢集提供高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢查清單： 使用容錯或負載平衡提供高可用性](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)。</span><span class="sxs-lookup"><span data-stu-id="f75f2-112">For more information about using Windows Clustering to provide high availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md).</span></span>  
  
-   <span data-ttu-id="f75f2-113">**測試的使用記錄傳送的 BizTalk Server 資料庫的復原。**</span><span class="sxs-lookup"><span data-stu-id="f75f2-113">**Test recovery of BizTalk Server databases using log shipping.**</span></span>  
  
     <span data-ttu-id="f75f2-114">您應該確認復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="f75f2-114">You should verify the recovery of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="f75f2-115">如需有關使用記錄傳送備份和還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[什麼是 BizTalk Server 記錄傳送？](../technical-guides/what-is-biztalk-server-log-shipping.md)本指南中或[記錄傳送](http://go.microsoft.com/fwlink/?LinkID=153450)(http://go.microsoft.com/fwlink/?LinkID=153450)。</span><span class="sxs-lookup"><span data-stu-id="f75f2-115">For more information about using log shipping to back up and restore [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md) in this guide or [Log Shipping](http://go.microsoft.com/fwlink/?LinkID=153450) (http://go.microsoft.com/fwlink/?LinkID=153450).</span></span>  
  
     <span data-ttu-id="f75f2-116">增加的可用性時，您應該遵循的步驟的檢查清單的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原，請參閱[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="f75f2-116">For a checklist of steps that you should follow to increase the availability of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment using disaster recovery, see [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75f2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f75f2-117">See Also</span></span>  
 [<span data-ttu-id="f75f2-118">增加可用性，以便讓 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f75f2-118">Increasing Availability for BizTalk Server</span></span>](../technical-guides/increasing-availability-for-biztalk-server.md)