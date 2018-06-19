---
title: 設定 EPM 執行緒集區大小 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e170e76-5151-4306-9473-5b68e815219a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54afa88b51876d0ee56f548f263be1b00c37967a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271134"
---
# <a name="setting-the-epm-threadpool-size"></a><span data-ttu-id="8d91a-102">設定 EPM 執行緒集區大小</span><span class="sxs-lookup"><span data-stu-id="8d91a-102">Setting the EPM Threadpool Size</span></span>
<span data-ttu-id="8d91a-103">本主題將說明如何設定「結束點管理員」(EPM) 的執行緒集區大小。</span><span class="sxs-lookup"><span data-stu-id="8d91a-103">This topic explains how to set the threadpool size for the End Point Manager (EPM).</span></span>  
  
 <span data-ttu-id="8d91a-104">在**進階**索引標籤中**主控件屬性**對話方塊中，沒有屬性，稱為**執行緒每一 CPU 的傳訊引擎數目上限**。</span><span class="sxs-lookup"><span data-stu-id="8d91a-104">On the **Advanced** tab in the **Host Properties** dialog box, there is a property called **Maximum number of messaging engine threads per CPU**.</span></span> <span data-ttu-id="8d91a-105">如需有關存取這個對話方塊中的指示，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。</span><span class="sxs-lookup"><span data-stu-id="8d91a-105">For instructions about accessing this dialog box, see [How to Create a New Host](../core/how-to-create-a-new-host.md).</span></span> <span data-ttu-id="8d91a-106">請使用此屬性來控制程序執行緒的集區大小，以便傳訊引擎用來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8d91a-106">Use this property to control the size of the pool of process threads that the messaging engine uses to process messages.</span></span> <span data-ttu-id="8d91a-107">此屬性的預設值為 20，表示傳訊引擎最多只會在伺服器的每一個 CPU 上使用 20 個執行緒。</span><span class="sxs-lookup"><span data-stu-id="8d91a-107">The default value for this property is 20, meaning that the messaging engine will use no more than 20 threads for each CPU on the server.</span></span>  
  
 <span data-ttu-id="8d91a-108">由於訊息批次會處理每個執行緒集區中，調整值**執行緒每一 CPU 的傳訊引擎數目上限**藉由變更伺服器上的資源使用率的 dynamics 可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="8d91a-108">Since batches of messages are processed by each thread in the pool, adjusting the value of **Maximum number of messaging engine threads per CPU** can affect performance by changing the dynamics of resource utilization on the server.</span></span> <span data-ttu-id="8d91a-109">如需有關執行緒集區的運作方式的詳細資訊，請參閱[使用 「 BizTalk 傳訊引擎](../core/using-the-biztalk-messaging-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="8d91a-109">For more information about how the threadpool works, see [Using the BizTalk Messaging Engine](../core/using-the-biztalk-messaging-engine.md).</span></span>  
  
 <span data-ttu-id="8d91a-110">經測試顯示，在其中的 CPU 或 SQL Server 會過度使用的情況下，減少的值**執行緒每一 CPU 的傳訊引擎數目上限**可能會導致網路輸送量優勢。</span><span class="sxs-lookup"><span data-stu-id="8d91a-110">Testing has shown that in cases where the CPU or the SQL Server is over utilized, decreasing the value of **Maximum number of messaging engine threads per CPU** can result in a net gain in throughput.</span></span> <span data-ttu-id="8d91a-111">例如，如果 MessageBox 資料庫伺服器顯示 CPU 的使用率超過 90%，或 SQL 鎖定等候時間攀升到 500-1000 毫秒以上，那麼減少集區中的執行緒數目，就可以降低對 SQL Server 進行連線的總次數，因此會提升訊息處理的效率。</span><span class="sxs-lookup"><span data-stu-id="8d91a-111">For example, in cases where the MessageBox database server exhibits CPU utilization above 90% or the SQL lock wait times are elevated above 500-1000 milliseconds, reducing the number of threads in the pool will reduce the overall number connections being made to SQL Server, which results in more efficient message processing.</span></span> <span data-ttu-id="8d91a-112">在某些情況下，將最大執行緒集區大小設定成像是 2 這樣低的值，可以在輸送量方面帶來可觀的效益。</span><span class="sxs-lookup"><span data-stu-id="8d91a-112">In some cases, setting the maximum thread pool size to a value as low as 2 can result in measurable throughput gain.</span></span>  
  
## <a name="recommendation"></a><span data-ttu-id="8d91a-113">建議</span><span class="sxs-lookup"><span data-stu-id="8d91a-113">Recommendation</span></span>  
 <span data-ttu-id="8d91a-114">當最佳化 BizTalk Server 安裝，建議您微調您的設定的值**執行緒每一 CPU 的傳訊引擎數目上限**。</span><span class="sxs-lookup"><span data-stu-id="8d91a-114">When optimizing a BizTalk Server installation, it is recommended that you fine tune the value you set for **Maximum number of messaging engine threads per CPU**.</span></span>  <span data-ttu-id="8d91a-115">當您嘗試降低 MessageBox 資料庫伺服器的使用率時，請考慮降低這個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8d91a-115">When you try to reduce the utilization of the MessageBox database server, consider reducing the value of this property.</span></span>  
  
 <span data-ttu-id="8d91a-116">當 BizTalk server 或 MessageBox 資料庫伺服器的使用率不高，並套用額外的負載不會導致更多的輸送量時，請嘗試增加的值**執行緒每一 CPU 的傳訊引擎數目上限**若要充分利用未使用的資源。</span><span class="sxs-lookup"><span data-stu-id="8d91a-116">When the BizTalk server or the MessageBox database server is not highly utilized, and applying additional load does not result in additional throughput, try increasing the value of **Maximum number of messaging engine threads per CPU** to take advantage of underutilized resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d91a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d91a-117">See Also</span></span>  
 <span data-ttu-id="8d91a-118">[如何建立新的主機](../core/how-to-create-a-new-host.md) </span><span class="sxs-lookup"><span data-stu-id="8d91a-118">[How to Create a New Host](../core/how-to-create-a-new-host.md) </span></span>  
 [<span data-ttu-id="8d91a-119">使用 「 BizTalk 傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="8d91a-119">Using the BizTalk Messaging Engine</span></span>](../core/using-the-biztalk-messaging-engine.md)