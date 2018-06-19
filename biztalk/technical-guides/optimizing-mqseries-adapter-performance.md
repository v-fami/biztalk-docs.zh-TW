---
title: MQSeries 配接器效能最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a46455c-a8d2-4427-99bb-4e3c6dbd9566
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d4a2bd1f2cfa338d31fd574879d73249d74d08b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299126"
---
# <a name="optimizing-mqseries-adapter-performance"></a><span data-ttu-id="18085-102">MQSeries 配接器效能最佳化</span><span class="sxs-lookup"><span data-stu-id="18085-102">Optimizing MQSeries Adapter Performance</span></span>
<span data-ttu-id="18085-103">使用下列設定來提高效能，可能的話，以設定 MQSeries 配接器。</span><span class="sxs-lookup"><span data-stu-id="18085-103">Configure the MQSeries adapter by using the following settings when possible to increase performance.</span></span>  
  
## <a name="adjust-the-value-for-the-mqseries-receive-adapter-polling-threads"></a><span data-ttu-id="18085-104">MQSeries 接收配接器輪詢執行緒調整值</span><span class="sxs-lookup"><span data-stu-id="18085-104">Adjust the value for the MQSeries receive adapter polling threads</span></span>  
 <span data-ttu-id="18085-105">增加為指定的值**執行緒**中**MQSeries 傳輸屬性**時設定 MQSeries 配接器接收位置。</span><span class="sxs-lookup"><span data-stu-id="18085-105">Increase the value specified for **Threads** in the **MQSeries Transport Properties** when configuring MQSeries adapter receive locations.</span></span> <span data-ttu-id="18085-106">增加此屬性從預設值為 2 到 5 的值將會大幅改善的訊息可以接收使用 MQSeries 配接器的速率。</span><span class="sxs-lookup"><span data-stu-id="18085-106">Increasing this property from the default value of 2 to a value of 5 will significantly improve the rate at which messages can be received using the MQSeries adapter.</span></span>  
  
## <a name="disable-transaction-support-on-mqseries-receive-locations-where-not-required"></a><span data-ttu-id="18085-107">停用交易支援 MQSeries 在接收位置在不需要</span><span class="sxs-lookup"><span data-stu-id="18085-107">Disable transaction support on MQSeries receive locations where not required</span></span>  
 <span data-ttu-id="18085-108">MQSeries 配接器的交易支援會帶來大量負擔。</span><span class="sxs-lookup"><span data-stu-id="18085-108">MQSeries adapter transaction support incurs significant overhead.</span></span> <span data-ttu-id="18085-109">如果交易支援不是一項業務需求，設定**交易支援**值**MQSeries 傳輸屬性** 對話方塊的預設值從**是**至**否**。</span><span class="sxs-lookup"><span data-stu-id="18085-109">If transaction support is not a business requirement, set the **Transaction Supported** value in the **MQSeries Transport Properties** dialog box from the default value of **Yes** to **No**.</span></span>  
  
## <a name="disable-ordered-delivery-of-messages-on-the-mqseries-adapter-when-not-required"></a><span data-ttu-id="18085-110">停用的訊息上 MQSeries 配接器時不需要排序的傳遞</span><span class="sxs-lookup"><span data-stu-id="18085-110">Disable Ordered delivery of messages on the MQSeries Adapter when not required</span></span>  
 <span data-ttu-id="18085-111">啟用此屬性會強制排序的訊息傳遞，因為它們會從接收或傳送至 MQSeries 佇列，但將會影響效能。</span><span class="sxs-lookup"><span data-stu-id="18085-111">Enabling this property will enforce ordered delivery of messages as they are received from or sent to the MQSeries queue but will affect performance.</span></span> <span data-ttu-id="18085-112">啟用 排序的傳遞時，傳訊執行階段會使用單一執行緒，從指定的 MQSeries 佇列接收訊息。</span><span class="sxs-lookup"><span data-stu-id="18085-112">When ordered delivery is enabled, the messaging runtime will use a single thread to receive messages from a given MQSeries queue.</span></span> <span data-ttu-id="18085-113">如果排序傳遞的訊息不是一項業務需求，然後進行變更的預設值**Ordered**屬性**MQSeries 傳輸屬性**設定為對話方塊**否排序**。</span><span class="sxs-lookup"><span data-stu-id="18085-113">If ordered delivery of messages is not a business requirement, then do not change the default value of **Ordered** property in the **MQSeries Transport Properties** dialog box which is set as **No Ordering**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18085-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18085-114">See Also</span></span>  
 [<span data-ttu-id="18085-115">BizTalk Server 效能最佳化</span><span class="sxs-lookup"><span data-stu-id="18085-115">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)