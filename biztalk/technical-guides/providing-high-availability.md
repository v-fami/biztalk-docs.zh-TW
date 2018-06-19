---
title: 提供高可用性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9240e776-555c-4c38-8b59-8fef1ba6a567
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4521981bc3df67553c244a55c91c1eb045c8e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302038"
---
# <a name="providing-high-availability"></a><span data-ttu-id="8c3a3-102">提供高可用性</span><span class="sxs-lookup"><span data-stu-id="8c3a3-102">Providing High Availability</span></span>
<span data-ttu-id="8c3a3-103">提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]藉由實作環境中的每個功能元件的備援的環境。</span><span class="sxs-lookup"><span data-stu-id="8c3a3-103">High availability is provided for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by implementing redundancy for each functional component in the environment.</span></span> <span data-ttu-id="8c3a3-104">BizTalk 主控件的複本可藉由安裝執行的多部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組中，然後設定在一個以上的執行的電腦上執行主控件執行個體中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="8c3a3-104">Redundancy for a BizTalk Host can be accomplished by installing multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a BizTalk group and then configuring instances of the host to run on more than one of the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="8c3a3-105">中的其他元件的備援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境可藉由設定的元件中的資源[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集。</span><span class="sxs-lookup"><span data-stu-id="8c3a3-105">Redundancy for other components in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment can be accomplished by configuring the components as resources in a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8c3a3-106">也會調節設定 BizTalk 主控件中的資源[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集中，建議您以特定 BizTalk 配接器提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="8c3a3-106"> also accommodates configuring BizTalk Hosts as resources in a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, which is recommended to provide high availability for certain BizTalk adapters.</span></span>  
  
 <span data-ttu-id="8c3a3-107">本節說明如何以提供高可用性的功能性元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="8c3a3-107">This section describes how to provide high availability for the functional components in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c3a3-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="8c3a3-108">In This Section</span></span>  
  
-   [<span data-ttu-id="8c3a3-109">規劃高 Availability2</span><span class="sxs-lookup"><span data-stu-id="8c3a3-109">Planning for High Availability2</span></span>](../technical-guides/planning-for-high-availability2.md)  
  
-   [<span data-ttu-id="8c3a3-110">BizTalk 主控件的高可用性</span><span class="sxs-lookup"><span data-stu-id="8c3a3-110">High Availability for BizTalk Hosts</span></span>](../technical-guides/high-availability-for-biztalk-hosts.md)  
  
-   [<span data-ttu-id="8c3a3-111">資料庫的高可用性</span><span class="sxs-lookup"><span data-stu-id="8c3a3-111">High Availability for Databases</span></span>](../technical-guides/high-availability-for-databases.md)  
  
-   [<span data-ttu-id="8c3a3-112">主要密碼伺服器的高可用性</span><span class="sxs-lookup"><span data-stu-id="8c3a3-112">High Availability for the Master Secret Server</span></span>](../technical-guides/high-availability-for-the-master-secret-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c3a3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c3a3-113">See Also</span></span>  
 [<span data-ttu-id="8c3a3-114">嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="8c3a3-114">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)