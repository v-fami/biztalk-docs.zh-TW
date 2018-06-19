---
title: 如何管理多個接收位置使用 MSMQ 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, threads
- receive locations, multiple
- threads
- receive locations, MSMQ adapters
- receive locations, threads
- configuring [MSMQ adapters], receive locations
ms.assetid: 5b2ee043-bcc9-443b-84b0-df7f487159eb
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72438551d2ecab09b918808d43e7d7de6d600677
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253806"
---
# <a name="how-to-manage-multiple-receive-locations-using-the-msmq-adapter"></a><span data-ttu-id="109f4-102">如何使用 MSMQ 配接器管理多個接收位置</span><span class="sxs-lookup"><span data-stu-id="109f4-102">How to Manage Multiple Receive Locations Using the MSMQ Adapter</span></span>
<span data-ttu-id="109f4-103">為了要增加效能，MSMQ 配接器為多執行緒。</span><span class="sxs-lookup"><span data-stu-id="109f4-103">To increase performance, the MSMQ adapter is multithreaded.</span></span> <span data-ttu-id="109f4-104">若您有多個接收位置，可能沒有足夠的執行緒供所有接收位置使用。</span><span class="sxs-lookup"><span data-stu-id="109f4-104">If you have many receive locations, there may not be enough threads available for all the receive locations.</span></span> <span data-ttu-id="109f4-105">如此會使部分接收位置無法提取訊息。</span><span class="sxs-lookup"><span data-stu-id="109f4-105">This prevents some of the receive locations from picking up messages.</span></span> <span data-ttu-id="109f4-106">有三種方式可解決此問題：</span><span class="sxs-lookup"><span data-stu-id="109f4-106">There are three ways to solve this problem:</span></span>  
  
-   <span data-ttu-id="109f4-107">將 BizTalk 主控件新增到您的電腦，並將接收位置分配給主控件。</span><span class="sxs-lookup"><span data-stu-id="109f4-107">Add BizTalk Hosts to your computer and divide the receive locations among the hosts.</span></span> <span data-ttu-id="109f4-108">新增主控件可提供更多執行緒給接收位置使用。</span><span class="sxs-lookup"><span data-stu-id="109f4-108">Adding hosts makes more threads available for the receive locations.</span></span>  
  
-   <span data-ttu-id="109f4-109">設定**序列處理**屬性`True`上每個接收位置。</span><span class="sxs-lookup"><span data-stu-id="109f4-109">Set the **Serial Processing** property to `True` on each receive location.</span></span> <span data-ttu-id="109f4-110">將屬性設為 `True`，即可指派單一執行緒給各個接收位置。</span><span class="sxs-lookup"><span data-stu-id="109f4-110">Setting the property to `True` assigns a single thread to each receive location.</span></span> <span data-ttu-id="109f4-111">如此可在集區中保留較多可用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="109f4-111">This leaves more threads available in the pool.</span></span> <span data-ttu-id="109f4-112">但是，這樣也可能會導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="109f4-112">However, this may also cause a decrease in performance.</span></span>  
  
-   <span data-ttu-id="109f4-113">修改登錄以增加 MSMQ 配接器接收處理常式的主控件可用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="109f4-113">Modify the registry to increase the number of threads that are available to the host for the MSMQ adapter receive handler.</span></span> <span data-ttu-id="109f4-114">如需詳細資訊，請參閱**修改主控件的 CLR 裝載執行緒值**區段[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="109f4-114">For more information see the **Modify the CLR Hosting thread values for the host** section of [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="109f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="109f4-115">See Also</span></span>  
 [<span data-ttu-id="109f4-116">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="109f4-116">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)