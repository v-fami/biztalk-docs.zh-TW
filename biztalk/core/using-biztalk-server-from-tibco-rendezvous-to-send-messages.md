---
redirect_url: /biztalk/core/using-tibco-rendezvous-send-ports-from-biztalk-server/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: d4a4f4fce200089db0e29d09b3ea49af00f3792f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014493"
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-send-messages"></a><span data-ttu-id="2a76a-101">從 TIBCO Rendezvous 使用 BizTalk Server 傳送訊息</span><span class="sxs-lookup"><span data-stu-id="2a76a-101">Using BizTalk Server from TIBCO Rendezvous to Send Messages</span></span>
<span data-ttu-id="2a76a-102">Microsoft BizTalk Adapter for TIBCO Rendezvous 使用非同步 API (Transport.Send)。</span><span class="sxs-lookup"><span data-stu-id="2a76a-102">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send).</span></span> <span data-ttu-id="2a76a-103">您可以使用訊息內容屬性指定配接器傳送的訊息種類：</span><span class="sxs-lookup"><span data-stu-id="2a76a-103">You can specify what kind of message the adapter sends using a message context property:</span></span>  
  
-   <span data-ttu-id="2a76a-104">**結構化**: 配接器會產生 TIBRVMSG_MSG 結構化的訊息時，根據從 BizTalk Server 接收的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="2a76a-104">**Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server.</span></span> <span data-ttu-id="2a76a-105">(\*)</span><span class="sxs-lookup"><span data-stu-id="2a76a-105">(\*)</span></span>  
  
 <span data-ttu-id="2a76a-106">如果 BizTalk Server 傳送的訊息中有欄位名稱超過 127 個字元，BizTalk Adapter for TIBCO Rendezvous 會將名稱截斷至 TIBCO Rendezvous 的欄位名稱大小上限 (即 127)。</span><span class="sxs-lookup"><span data-stu-id="2a76a-106">If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.</span></span>  
  
 <span data-ttu-id="2a76a-107">如果提供 `reply subject name` 屬性，會用來設定 TIBCO Rendezvous 訊息的回覆主旨。</span><span class="sxs-lookup"><span data-stu-id="2a76a-107">If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message.</span></span> <span data-ttu-id="2a76a-108">這是假設接收埠設為接聽回覆並將它轉寄至 BizTalk Server，或一些其他的 TIBCO Rendezvous 程式會處理回覆。</span><span class="sxs-lookup"><span data-stu-id="2a76a-108">It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.</span></span>  
  
 <span data-ttu-id="2a76a-109">服務、精靈與網路這三者構成傳輸組態。</span><span class="sxs-lookup"><span data-stu-id="2a76a-109">The triplet (service, daemon, network) makes up the transport configuration.</span></span> <span data-ttu-id="2a76a-110">傳輸組態空白 (預設值) 時，則會透過預設的傳輸物件傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="2a76a-110">An empty (default) transport configuration results in a message being sent through the default transport object.</span></span>  
  
 <span data-ttu-id="2a76a-111">如果未指定字碼頁，配接器會使用 UTF-8 編碼 (字碼頁 65001)。</span><span class="sxs-lookup"><span data-stu-id="2a76a-111">If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001).</span></span> <span data-ttu-id="2a76a-112">傳輸器端不支援認證訊息。</span><span class="sxs-lookup"><span data-stu-id="2a76a-112">Certified Messages are not supported on the transmitter side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a76a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a76a-113">See Also</span></span>  
 <span data-ttu-id="2a76a-114">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="2a76a-114">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="2a76a-115">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="2a76a-115">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)