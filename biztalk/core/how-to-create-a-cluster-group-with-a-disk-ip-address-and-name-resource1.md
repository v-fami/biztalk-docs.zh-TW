---
title: "如何建立叢集群組的磁碟，IP 位址，並命名 Resource1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b361f721-60db-485e-9ce3-48a6871ebd79
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63310706742ffcc10de5266dda7053da79fc04fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource"></a><span data-ttu-id="8b008-102">如何使用磁碟、IP 位址及名稱資源建立叢集群組</span><span class="sxs-lookup"><span data-stu-id="8b008-102">How to Create a Cluster Group with a Disk, IP Address, and Name Resource</span></span>
<span data-ttu-id="8b008-103">為叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]元件以及相依性能透過 NetBIOS，叢集網路上可供存取，**網路名稱**相同叢集群組中，必須建立資源。</span><span class="sxs-lookup"><span data-stu-id="8b008-103">For clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components and dependencies to be accessible over the network via NetBIOS, a clustered **Network Name** resource must be created in same cluster group.</span></span> <span data-ttu-id="8b008-104">叢集網路名稱資源可供存取，透過 TCP/IP 通訊協定， **IP 位址**相同叢集群組中，必須建立資源。</span><span class="sxs-lookup"><span data-stu-id="8b008-104">For a clustered Network Name resource to be accessible via the TCP/IP protocol, an **IP Address** resource must be created in the same cluster group as well.</span></span> <span data-ttu-id="8b008-105">某些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相依性還必須使用叢集**實體磁碟**資源才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="8b008-105">Some [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependencies also require the use of a clustered **Physical Disk** resource to function correctly.</span></span> <span data-ttu-id="8b008-106">若要建立的叢集群組**實體磁碟**， **IP 位址**和**網路名稱**資源，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8b008-106">To create a cluster group with a **Physical Disk**, **IP Address** and **Network Name** resource follow these steps:</span></span>  
  
### <a name="to-create-a-service-or-application-with-a-physical-disk-ip-address-and-network-name-resource"></a><span data-ttu-id="8b008-107">若要建立與實體磁碟、 IP 位址和網路名稱資源的服務或應用程式</span><span class="sxs-lookup"><span data-stu-id="8b008-107">To create a service or application with a Physical Disk, IP Address, and Network Name resource</span></span>  
  
1.  <span data-ttu-id="8b008-108">在 Windows 中，按一下 **啟動**，**程式**，**系統管理工具**，然後**容錯移轉叢集管理**啟動容錯移轉叢集管理程式。</span><span class="sxs-lookup"><span data-stu-id="8b008-108">In Windows, click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.</span></span>  
  
2.  <span data-ttu-id="8b008-109">容錯移轉所有的服務和應用程式執行容錯移轉叢集管理的叢集節點。</span><span class="sxs-lookup"><span data-stu-id="8b008-109">Fail over all services and applications to the cluster node that you are running Failover Cluster Management on.</span></span> <span data-ttu-id="8b008-110">若要容錯移轉服務或應用程式，以滑鼠右鍵按一下服務或應用程式容錯移轉叢集管理的左窗格中，指向**將此服務或應用程式到另一個節點移動**按一下來選取目的地節點。</span><span class="sxs-lookup"><span data-stu-id="8b008-110">To fail over a service or application, right click the service or application in the left pane of Failover Cluster Management, point to **Move this service or application to another node** and click to select the destination node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b008-111">裝載執行中叢集資源的叢集節點就是所謂**active**節點。</span><span class="sxs-lookup"><span data-stu-id="8b008-111">The cluster node that hosts running cluster resources is also known as the **active** node.</span></span> <span data-ttu-id="8b008-112">裝載非執行中叢集資源的叢集節點就是所謂**被動**節點。</span><span class="sxs-lookup"><span data-stu-id="8b008-112">The cluster node that hosts non-running cluster resources is also known as the **passive** node.</span></span>  
  
3.  <span data-ttu-id="8b008-113">在左側窗格中，以滑鼠右鍵按一下**服務和應用程式**，按一下 **設定服務或應用程式**以啟動 高可用性精靈，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="8b008-113">In the left-hand pane, right-click **Services and Applications**, click **Configure a Service or Application** to launch the High Availability Wizard, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8b008-114">按一下以選取**檔案伺服器**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8b008-114">Click to select **File Server** and click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b008-115">選取**檔案伺服器**此時會完成，因為直接的方法具有磁碟資源建立叢集群組。</span><span class="sxs-lookup"><span data-stu-id="8b008-115">Selecting **File Server** at this point is done as a straightforward way to create a cluster group with a disk resource.</span></span>  
  
5.  <span data-ttu-id="8b008-116">在**用戶端存取點**高可用性精靈] 的頁面上，輸入唯一的網路名稱**名稱**方塊中，例如*BizTalkCluster*，輸入可用的 IP在解決**位址**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8b008-116">On the **Client Access Point** page of the High Availability Wizard enter a unique network name into the **Name** box, for example *BizTalkCluster*, enter an available IP address under **Address**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="8b008-117">在**選取儲存體**頁面中，按一下以選取可用的磁碟資源，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8b008-117">On the **Select Storage** page, click to select an available disk resource and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="8b008-118">在**確認**頁面上，按一下**下一步**建立叢集群組。</span><span class="sxs-lookup"><span data-stu-id="8b008-118">On the **Confirmation** page click **Next** to create the cluster group.</span></span>  
  
8.  <span data-ttu-id="8b008-119">在**摘要**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="8b008-119">On the **Summary** page click **Finish**.</span></span>