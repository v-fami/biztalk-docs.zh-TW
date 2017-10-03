---
title: "TIBCO Rendezvous 限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TIBCO Rendezvous, limitations
ms.assetid: 8e210457-2887-43f9-a249-be1daa6ee4eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717188e42450d13dee92364cd9c673aaaf48eaf6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-limitations"></a><span data-ttu-id="dd08c-102">TIBCO Rendezvous 限制</span><span class="sxs-lookup"><span data-stu-id="dd08c-102">TIBCO Rendezvous Limitations</span></span>
<span data-ttu-id="dd08c-103">在 TIBCO Rendezvous 中，並不保證欄位名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dd08c-103">In TIBCO Rendezvous, field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="dd08c-104">如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。</span><span class="sxs-lookup"><span data-stu-id="dd08c-104">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
 <span data-ttu-id="dd08c-105">其他限制還包括：</span><span class="sxs-lookup"><span data-stu-id="dd08c-105">Other limitations include the following:</span></span>  
  
-   <span data-ttu-id="dd08c-106">不會提供欄位排序。</span><span class="sxs-lookup"><span data-stu-id="dd08c-106">Field ordering/sorting is not provided.</span></span>  
  
-   <span data-ttu-id="dd08c-107">根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。</span><span class="sxs-lookup"><span data-stu-id="dd08c-107">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="dd08c-108">BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="dd08c-108">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
-   <span data-ttu-id="dd08c-109">不支援對精靈的安全連線。</span><span class="sxs-lookup"><span data-stu-id="dd08c-109">Secure connection to daemons is not supported.</span></span>  
  
-   <span data-ttu-id="dd08c-110">不支援自訂資料型別。</span><span class="sxs-lookup"><span data-stu-id="dd08c-110">Custom data types are not supported.</span></span>  
  
-   <span data-ttu-id="dd08c-111">傳輸端不支援「認證傳訊」。</span><span class="sxs-lookup"><span data-stu-id="dd08c-111">Certified Messaging is not supported on the transmit side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd08c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd08c-112">See Also</span></span>  
 <span data-ttu-id="dd08c-113">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="dd08c-113">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="dd08c-114">快速入門</span><span class="sxs-lookup"><span data-stu-id="dd08c-114">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)