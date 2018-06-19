---
title: 驗證的處理序之間的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PID
- security, warnings
- processing, messages
- processing, security
- messages, processing
- security, messages
- MessageBox database, authenticating
- SSID
- authenticating, warnings
ms.assetid: fa746ee3-fc22-4e63-a5cc-8bc0cbeb536b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c54fb463353ed6551dcbf5764fae05e63fdb778
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231302"
---
# <a name="authentication-of-messages-between-processes"></a><span data-ttu-id="6459e-102">驗證的處理序之間的訊息</span><span class="sxs-lookup"><span data-stu-id="6459e-102">Authentication of Messages Between Processes</span></span>
<span data-ttu-id="6459e-103">下圖顯示 BizTalk Server 中可讓您在不同 BizTalk 主控件之間驗證訊息的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6459e-103">The following figure shows the security features in BizTalk Server that enable you to authenticate messages between different BizTalk hosts.</span></span>  
  
 <span data-ttu-id="6459e-104">![驗證訊息的安全性功能](../core/media/ebiz-plan-secoverview-auth-process.gif "ebiz_plan_secoverview_auth_process")</span><span class="sxs-lookup"><span data-stu-id="6459e-104">![Security features authenticating messages](../core/media/ebiz-plan-secoverview-auth-process.gif "ebiz_plan_secoverview_auth_process")</span></span>  
<span data-ttu-id="6459e-105">BizTalk Server 用來驗證程序之間訊息的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6459e-105">Security features BizTalk Server uses to authenticate messages between processes.</span></span>  
  
 <span data-ttu-id="6459e-106">在 BizTalk Server 接收訊息、解密和驗證訊息，以及取得有效的合作對象識別碼 (PID) 和憑證以識別訊息傳送者之後，MessageBox 資料庫即可開始驗證訊息所符合的訂閱，然後將這個訊息傳送給其他主控件做進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="6459e-106">After BizTalk Server receives a message, decrypts and validates the message, and has a valid party ID (PID) and certificate to identity the sender of the message, the MessageBox database is ready to verify the subscriptions that the message matches, and to send this message to other hosts for further processing.</span></span>  
  
 <span data-ttu-id="6459e-107">訊息從一個程序流動到另一個程序時，通常必須將訊息原始傳送者的識別傳遞至下游程序以供授權、合作對象解析和傳送者的相關商務邏輯運作之用。</span><span class="sxs-lookup"><span data-stu-id="6459e-107">As a message flows from one process to another, it is often necessary to pass the identity of the original sender of the message to downstream processes for authorization, party resolution, and business logic relating to the sender.</span></span> <span data-ttu-id="6459e-108">不過，如果讓所有主控件流通這項資訊，而沒有使用某種安全性或信任機制，將會大幅增加必須確認所有使用者物件和程式碼 (例如，協調流程、配接器、管線元件、運算質等) 是否可信賴的需求。</span><span class="sxs-lookup"><span data-stu-id="6459e-108">However, enabling all hosts to flow this information without some type of security or trust mechanism would greatly increase the need to verify that all user objects and code (for example, orchestrations, adapters, pipeline components, functoids) are trustworthy.</span></span>  
  
 <span data-ttu-id="6459e-109">為了提供區別使用者物件和程式碼信任層級的方法，BizTalk Server 提供「驗證信任」做為主控件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6459e-109">To provide the means to differentiate the level of trust for user objects and code, BizTalk Server provides Authentication Trust as a property of hosts.</span></span> <span data-ttu-id="6459e-110">當 MessageBox 資料庫從尚未設定為驗證信任的主控件接收訊息時，MessageBox 資料庫會以 Guest 識別碼覆寫 PID，而以主控件執行個體執行時所用的服務帳戶來覆寫 SSID。</span><span class="sxs-lookup"><span data-stu-id="6459e-110">When the MessageBox database receives a message from a host that has not been set as authentication trusted, the MessageBox database overwrites the PID with the guest ID, and overwrites the SSID with the service account that the host instance is running as.</span></span> <span data-ttu-id="6459e-111">當主控件標示為信任的驗證時，BizTalk 允許主控件指定任何傳送者 SID (SSID) 以及在排入 MessageBox 資料庫佇列之訊息上的任何合作對象識別碼 (PID)。</span><span class="sxs-lookup"><span data-stu-id="6459e-111">When a host is marked as authentication trusted, BizTalk enables the host to specify any sender SID (SSID) and any party ID (PID) on messages that it queues to the MessageBox database.</span></span>  
  
 <span data-ttu-id="6459e-112">藉由指定哪些主控件可信任而哪些不可信任，您就能定義可否信任使用者物件和程式碼的安全性範圍。</span><span class="sxs-lookup"><span data-stu-id="6459e-112">By specifying which hosts are trusted and which are not, you can define security boundaries in which user objects and code can be trusted or not trusted.</span></span> <span data-ttu-id="6459e-113">也就是說，部署到設定為驗證信任主控件中的使用者物件和程式碼，必須比部署到尚未設定為驗證信任主控件中的使用者物件和程式碼更可信賴。</span><span class="sxs-lookup"><span data-stu-id="6459e-113">That is, user objects and code deployed into hosts that have been set to Authentication Trusted need to be more trustworthy than user objects and code deployed to hosts that have not been set to Authentication Trusted.</span></span> <span data-ttu-id="6459e-114">如需如何設定驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6459e-114">For more information about how to configure authentication trusted host, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
 <span data-ttu-id="6459e-115">MessageBox 資料庫接收訊息時，BizTalk Server 會採取下列步驟以強制對傳送訊息至 MessageBox 資料庫的主控件執行個體使用驗證信任：</span><span class="sxs-lookup"><span data-stu-id="6459e-115">When the MessageBox database receives a message, BizTalk Server takes the following steps to enforce the authentication trust of the host instance sending the message to the MessageBox database:</span></span>  
  
1.  <span data-ttu-id="6459e-116">MessageBox 資料庫首先檢查 SSID 是否屬於信任主控件的主控件執行個體服務帳戶，以判斷傳送訊息的主控件是否已經設定為信任的驗證。</span><span class="sxs-lookup"><span data-stu-id="6459e-116">The MessageBox database first determines whether the host sending the message has been set as authentication trusted by checking that the SSID is that of a host instance service account for a trusted host.</span></span>  
  
2.  <span data-ttu-id="6459e-117">如果傳送訊息至 MessageBox 資料庫的主控件是信任的驗證，MessageBox 資料庫便會將 SSID 和 PID 如實保留在訊息內容中，除非其為空白。</span><span class="sxs-lookup"><span data-stu-id="6459e-117">If the host that is sending the message to the MessageBox database is authentication trusted, the MessageBox database leaves the SSID and PID in the message context "as is," unless they are empty.</span></span> <span data-ttu-id="6459e-118">如果 SSID 為空白，則 MessageBox 資料庫會填入呼叫程序的 SID，也稱為主控件 SID (HSID)。</span><span class="sxs-lookup"><span data-stu-id="6459e-118">If the SSID is empty, the MessageBox database populates it with the SID of the calling process, also known as the host SID (HSID).</span></span> <span data-ttu-id="6459e-119">如果 PID 為空白，則會將 PID 設定為 Guest 識別碼。</span><span class="sxs-lookup"><span data-stu-id="6459e-119">If the PID is empty, it sets the PID to the guest ID.</span></span>  
  
3.  <span data-ttu-id="6459e-120">如果傳送訊息至 MessageBox 資料庫的主控件尚未設定為信任的驗證，則不論這些欄位是否已有內容填入，都會以 HSID 填入 SSID，並將 PID 設定為 Guest。</span><span class="sxs-lookup"><span data-stu-id="6459e-120">If the host that is sending the message to the MessageBox database has not been set as authentication trusted, the SSID is populated with the HSID, and the PID is set to Guest, regardless of whether these fields were already populated.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6459e-121">如果要讓下游程序知道訊息原始傳送者的 SSID 和 PID，您必須將訊息傳遞時會經過的所有主控件都設定為信任的驗證。</span><span class="sxs-lookup"><span data-stu-id="6459e-121">If you want a downstream process to know the SSID and PID of the original sender of the message, you must set all hosts that the message passes through as authentication trusted.</span></span> <span data-ttu-id="6459e-122">此外，像是在收到訊息時，隨後將之用於協調流程以建構輸出訊息的這種情況下，則必須明確地將輸入訊息上收到的 SSID 和 PID 當做屬性加入輸出訊息，才能使這些識別流通。</span><span class="sxs-lookup"><span data-stu-id="6459e-122">In addition, in cases such as when the message is received and subsequently used to construct outbound messages in an orchestration, the SSID and PID received on inbound messages must be explicitly added as a property to outbound messages in order to flow these identities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6459e-123">如果您將管線執行所在的主控件設定為信任的驗證，BizTalk Server 便會將管線視為信任的環境。</span><span class="sxs-lookup"><span data-stu-id="6459e-123">If you configured the host where a pipeline is running as authentication trusted, BizTalk Server considers the pipeline to be a trusted environment.</span></span> <span data-ttu-id="6459e-124">因此，確認正執行於主控件之 BizTalk 管線所包含的任何驗證信任的自訂元件本身是否也是受信任的，極其重要。</span><span class="sxs-lookup"><span data-stu-id="6459e-124">Therefore, it is extremely important that you verify that any custom components that are included in a BizTalk pipeline that is running on a host that is authentication trusted are also trusted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6459e-125">對於驗證為信任的主控件以及未驗證為信任的主控件，不可以使用相同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="6459e-125">You cannot use the same service account for hosts that are authentication trusted and for hosts that are not authentication trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6459e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6459e-126">See Also</span></span>  
 <span data-ttu-id="6459e-127">[輸入訊息驗證](../core/inbound-message-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="6459e-127">[Inbound Message Authentication](../core/inbound-message-authentication.md) </span></span>  
 <span data-ttu-id="6459e-128">[輸出訊息保護](../core/outbound-message-protection.md) </span><span class="sxs-lookup"><span data-stu-id="6459e-128">[Outbound Message Protection](../core/outbound-message-protection.md) </span></span>  
 <span data-ttu-id="6459e-129">[驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="6459e-129">[Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) </span></span>  
 [<span data-ttu-id="6459e-130">授權訊息接收器</span><span class="sxs-lookup"><span data-stu-id="6459e-130">Authorizing the Receiver of a Message</span></span>](../core/authorizing-the-receiver-of-a-message.md)