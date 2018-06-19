---
title: MQSeries 配接器的高可用性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, MQSeries adapters
- MQSeries adapters, availability
- MQSeries adapters, performance
- high availability, MQSeries adapters
ms.assetid: 4339b10b-b35d-47c0-b78a-c60207e06c8e
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c0b6486e49cb2ccddfab37271a94a4ba7a6948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263230"
---
# <a name="mqseries-adapter-high-availability"></a><span data-ttu-id="12dfd-102">MQSeries 配接器的高可用性</span><span class="sxs-lookup"><span data-stu-id="12dfd-102">MQSeries Adapter High Availability</span></span>
<span data-ttu-id="12dfd-103">當您使用配接器時，可以使用下列方式來改善可用性：</span><span class="sxs-lookup"><span data-stu-id="12dfd-103">You can improve availability in the following ways when you use the adapter:</span></span>  
  
-   <span data-ttu-id="12dfd-104">為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定容錯裝載環境。</span><span class="sxs-lookup"><span data-stu-id="12dfd-104">Set up a fault-tolerant hosting environment for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="12dfd-105">搭配 IBM WebSphere MQ 使用 Windows 叢集。</span><span class="sxs-lookup"><span data-stu-id="12dfd-105">Use Windows Clustering with IBM WebSphere MQ.</span></span>  
  
 <span data-ttu-id="12dfd-106">如需有關容錯資訊和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)和[規劃您的平台容錯](../core/planning-your-platform-for-fault-tolerance.md)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助。</span><span class="sxs-lookup"><span data-stu-id="12dfd-106">For information about fault tolerance and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md) and [Planning Your Platform for Fault Tolerance](../core/planning-your-platform-for-fault-tolerance.md) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="12dfd-107">為確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries 配接器能夠與 MQSAgent 元件的遠端安裝通訊，請確定您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和已安裝 IBM WebSphere MQ 的伺服器上已經啟用網路 COM+ 存取。</span><span class="sxs-lookup"><span data-stu-id="12dfd-107">To ensure that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries Adapter is able to communicate with a remote installation of the MQSAgent component, ensure that you have enabled network COM+ access on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]and server where IBM WebSphere MQ is installed.</span></span> <span data-ttu-id="12dfd-108">如需有關啟用網路 COM + 存取的詳細資訊，請參閱 Microsoft 知識庫文章編號 817065"How to enable network COM + access in Windows Server 2003"位於[http://go.microsoft.com/fwlink/?LinkId=196580](http://go.microsoft.com/fwlink/?LinkId=196580)。</span><span class="sxs-lookup"><span data-stu-id="12dfd-108">For more information about enabling network COM+ access, see Microsoft Knowledge Base article number 817065, " How to enable network COM+ access in Windows Server 2003," available at [http://go.microsoft.com/fwlink/?LinkId=196580](http://go.microsoft.com/fwlink/?LinkId=196580).</span></span>  
  
 <span data-ttu-id="12dfd-109">不需要針對搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries 配接器使用的 MQSAgent (MQSAgent2) COM+ 應用程式進行叢集。</span><span class="sxs-lookup"><span data-stu-id="12dfd-109">There is no requirement to cluster the MQSAgent (MQSAgent2) COM+ application that is used with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries adapter.</span></span> <span data-ttu-id="12dfd-110">若要為此元件提供高可用性，請在每個叢集節點安裝此元件。</span><span class="sxs-lookup"><span data-stu-id="12dfd-110">To provide high availability for this component, install the component on each cluster node.</span></span> <span data-ttu-id="12dfd-111">若 COM+ 應用程式停止，則用戶端的下次呼叫將會啟動它。</span><span class="sxs-lookup"><span data-stu-id="12dfd-111">If the COM+ application stops, the next call from the client will start it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dfd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12dfd-112">See Also</span></span>  
 [<span data-ttu-id="12dfd-113">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="12dfd-113">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)