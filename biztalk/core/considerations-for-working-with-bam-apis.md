---
title: 使用 BAM Api 的考量事項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd8ccf63-6989-4ad6-a193-cf3043e9a466
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b00eb00013fefde42e1972b89a661d0a2ba0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237838"
---
# <a name="considerations-for-working-with-bam-apis"></a><span data-ttu-id="64e9d-102">使用 BAM API 的考量</span><span class="sxs-lookup"><span data-stu-id="64e9d-102">Considerations for Working with BAM APIs</span></span>
<span data-ttu-id="64e9d-103">在使用 "Microsoft.BizTalk.Bam.EventObservation.EventStream" 物件時，例如 DirectEventStream、BufferedEventStream、MessagingEventStream，或者是 OrchestrationEventStream，BAM 會在擷取里程碑時自動採用國際標準時間 (Coordinated Universal Time，UTC) 格式加以記錄 (亦稱為格林威治標準時間)。</span><span class="sxs-lookup"><span data-stu-id="64e9d-103">When using an  "Microsoft.BizTalk.Bam.EventObservation.EventStream" object, such as DirectEventStream, BufferedEventStream, MessagingEventStream, or OrchestrationEventStream, BAM captures milestones such that they are automatically recorded in Coordinated Universal Time (UTC) format (this is also referred to as Greenwich Mean Time).</span></span> <span data-ttu-id="64e9d-104">當您使用 API 將日期/時間傳送給 BAM 時，所收到的格式在傳送時尚未轉換為 UTC 格式。</span><span class="sxs-lookup"><span data-stu-id="64e9d-104">When you send date/times to BAM using the APIs they are received in the format sent with no conversion to UTC format.</span></span> <span data-ttu-id="64e9d-105">在開發 BAM 方案時，請將以下事項列入考量：</span><span class="sxs-lookup"><span data-stu-id="64e9d-105">You should take the following considerations into account when you are developing your BAM solutions:</span></span>  
  
-   <span data-ttu-id="64e9d-106">追蹤自 BizTalk Server 的資料是以 UTC 格式接收。</span><span class="sxs-lookup"><span data-stu-id="64e9d-106">Data traced from BizTalk Server is received in UTC format.</span></span> <span data-ttu-id="64e9d-107">這可能與來自事件資料流的其他資料格式不一致。</span><span class="sxs-lookup"><span data-stu-id="64e9d-107">This could be inconsistent with other data that comes from the event stream.</span></span>  
  
-   <span data-ttu-id="64e9d-108">如果您使用事件資料流 API 以本地時間格式來提供日期與時間追蹤資料，則 BAM 入口網站的資料會有錯誤，因為預期的 BAM 資料中，所有的時間都應為 UTC 格式。</span><span class="sxs-lookup"><span data-stu-id="64e9d-108">If you use the event stream APIs to provide date and time tracking data in local time format, the data in the BAM portal will be incorrect as the expectation is that all times in BAM data are in UTC format.</span></span>  
  
 <span data-ttu-id="64e9d-109">如果您現有的應用程式是使用本地時間，而您現在正打算升級並計畫使用 BAM 入口網站，則請務必將資料修改為符合 UTC 格式要求。</span><span class="sxs-lookup"><span data-stu-id="64e9d-109">If you have existing applications that use local time, and you are now upgrading and planning to use the BAM portal, you must modify your data to make it conform to UTC format.</span></span> <span data-ttu-id="64e9d-110">同時，您需要修改自訂應用程式以轉換成 UTC 格式。</span><span class="sxs-lookup"><span data-stu-id="64e9d-110">You also need to modify your custom application to convert to UTC format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e9d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64e9d-111">See Also</span></span>  
 [<span data-ttu-id="64e9d-112">實作 BAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="64e9d-112">Implementing BAM Solutions</span></span>](../core/implementing-bam-solutions.md)