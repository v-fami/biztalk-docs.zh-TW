---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: bcccc92430a73685ced9ad7259d8ec57dfc450b8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013229"
---
# <a name="tibco-rendezvous-limitations"></a><span data-ttu-id="f51c9-101">TIBCO Rendezvous 限制</span><span class="sxs-lookup"><span data-stu-id="f51c9-101">TIBCO Rendezvous Limitations</span></span>
<span data-ttu-id="f51c9-102">在 TIBCO Rendezvous 中，並不保證欄位名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f51c9-102">In TIBCO Rendezvous, field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="f51c9-103">如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。</span><span class="sxs-lookup"><span data-stu-id="f51c9-103">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
 <span data-ttu-id="f51c9-104">其他限制還包括：</span><span class="sxs-lookup"><span data-stu-id="f51c9-104">Other limitations include the following:</span></span>  
  
-   <span data-ttu-id="f51c9-105">不會提供欄位排序。</span><span class="sxs-lookup"><span data-stu-id="f51c9-105">Field ordering/sorting is not provided.</span></span>  
  
-   <span data-ttu-id="f51c9-106">根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。</span><span class="sxs-lookup"><span data-stu-id="f51c9-106">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="f51c9-107">BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="f51c9-107">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
-   <span data-ttu-id="f51c9-108">不支援對精靈的安全連線。</span><span class="sxs-lookup"><span data-stu-id="f51c9-108">Secure connection to daemons is not supported.</span></span>  
  
-   <span data-ttu-id="f51c9-109">不支援自訂資料型別。</span><span class="sxs-lookup"><span data-stu-id="f51c9-109">Custom data types are not supported.</span></span>  
  
-   <span data-ttu-id="f51c9-110">傳輸端不支援「認證傳訊」。</span><span class="sxs-lookup"><span data-stu-id="f51c9-110">Certified Messaging is not supported on the transmit side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51c9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f51c9-111">See Also</span></span>  
 <span data-ttu-id="f51c9-112">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="f51c9-112">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="f51c9-113">快速入門</span><span class="sxs-lookup"><span data-stu-id="f51c9-113">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)