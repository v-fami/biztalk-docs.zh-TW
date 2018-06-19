---
title: 傳送和接收訊息的安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, receiving
- messages, sending
- messages, processing
- security, messages
- security, message processing
- messages, security
ms.assetid: 9bcd01e4-245a-4f4c-b65c-89d7cd3d1b68
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1328eb98cbf94b85cda16eda431da197c6d0126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270598"
---
# <a name="security-for-sending-and-receiving-messages"></a><span data-ttu-id="54d88-102">傳送與接收訊息的安全性</span><span class="sxs-lookup"><span data-stu-id="54d88-102">Security for Sending and Receiving Messages</span></span>
<span data-ttu-id="54d88-103">下圖顯示當 BizTalk Server 接收、處理訊息以及將其傳送至其他應用程式或夥伴時，會發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="54d88-103">The following figure shows what happens to a message as BizTalk Server receives it, processes it, and sends it to another application or partner.</span></span>  
  
 <span data-ttu-id="54d88-104">![安全訊息的安全性功能](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span><span class="sxs-lookup"><span data-stu-id="54d88-104">![Security features for secure messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span></span>  
<span data-ttu-id="54d88-105">在訊息的整個存留期間使用安全性功能</span><span class="sxs-lookup"><span data-stu-id="54d88-105">Security features used throughout the lifetime of a message</span></span>  
  
1.  <span data-ttu-id="54d88-106">配接器的接收位置會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="54d88-106">The receive location for the adapter receives the message.</span></span> <span data-ttu-id="54d88-107">依通訊協定而定，配接器會執行傳送者的通訊協定層級驗證，以識別代表訊息傳送者的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="54d88-107">Depending on the protocol, the adapter does protocol-level authentication of the sender to identify a Windows user account that represents the sender of the message.</span></span>  
  
2.  <span data-ttu-id="54d88-108">配接器接著將訊息傳遞給管線；如果配接器中沒有發生訊息層級驗證，便會在此管線中進行這個驗證。</span><span class="sxs-lookup"><span data-stu-id="54d88-108">The adapter then passes the message to the pipeline, where message-level authentication takes place if it has not already happened in the adapter.</span></span>  
  
    1.  <span data-ttu-id="54d88-109">在「解碼」階段，管線會解密訊息並使用附加於訊息的憑證或本機電腦「其他人」憑證存放區中設定的憑證來驗證簽章的有效性。</span><span class="sxs-lookup"><span data-stu-id="54d88-109">In the Decode stage, the pipeline decrypts the message and verifies the validity of the signature with the certificate attached to the message, or the one configured in the Other People certificate store of the local computer.</span></span> <span data-ttu-id="54d88-110">管線驗證簽章之後，解碼元件會上至信任根憑證授權單位 (CA)，對憑證鏈結進行驗證。</span><span class="sxs-lookup"><span data-stu-id="54d88-110">After the pipeline validates the signature, the decoding component validates the certificate chain up to a trusted root Certificate Authority (CA).</span></span> <span data-ttu-id="54d88-111">如果您設定管線以解碼 S/MIME 訊息，而且傳送者已經使用 S/MIME 來加密訊息，則 MIME/SMIME 解碼器會驗證訊息的簽章，並使用憑證來識別傳送者。</span><span class="sxs-lookup"><span data-stu-id="54d88-111">If you configure the pipeline to decode S/MIME messages, and the sender encrypted the message using S/MIME, the MIME/SMIME decoder verifies the signature of the message, and uses the certificate to identify the sender.</span></span> <span data-ttu-id="54d88-112">如需如何使用 MIME/SMIME 解碼器管線元件的詳細資訊，請參閱[實作訊息安全性](../core/implementing-message-security.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-112">For more information about how to use MIME/SMIME decoder pipeline components, see [Implementing Message Security](../core/implementing-message-security.md).</span></span>  
  
    2.  <span data-ttu-id="54d88-113">在「合作對象解析」階段，BizTalk Server 會使用憑證資訊和從通訊協定層級驗證取得的「傳送者安全性識別碼」(SSID)，來判斷訊息傳送者是否為系統中辨識的合作對象。</span><span class="sxs-lookup"><span data-stu-id="54d88-113">In the Party Resolution stage, BizTalk Server uses the certificate information and the Sender Security ID (SSID) obtained from protocol-level authentication to determine whether the sender of the message is a recognized party in the system.</span></span> <span data-ttu-id="54d88-114">傳送者 SSID 是由配接器所驗證的使用者的完整格式名稱。</span><span class="sxs-lookup"><span data-stu-id="54d88-114">The Sender SSID is the qualified name of the user authenticated by the adapter.</span></span> <span data-ttu-id="54d88-115">例如，</span><span class="sxs-lookup"><span data-stu-id="54d88-115">For example.</span></span> <span data-ttu-id="54d88-116">如果 BizTalk Server 使用 Windows 驗證以透過 HTTP 配接器接收訊息，則傳送者 SSID 即是「網域\使用者名稱」。</span><span class="sxs-lookup"><span data-stu-id="54d88-116">If BizTalk Server receives the message by way of the HTTP adapter using Windows authentication, then the sender SSID is domain\username.</span></span> <span data-ttu-id="54d88-117">BizTalk Server 會指派合作對象識別碼 (PID) 給訊息，該識別碼會是已辨識之合作對象的合作對象識別碼或訪客識別碼。</span><span class="sxs-lookup"><span data-stu-id="54d88-117">BizTalk Server assigns a Party ID (PID) to the message, which is either the party ID of a recognized party, or a guest ID.</span></span> <span data-ttu-id="54d88-118">如需如何使用合作對象解析元件的詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-118">For more information about how to use party resolution component, see [Using Certificates for Party Resolution](../core/using-certificates-for-party-resolution.md).</span></span>  
  
    3.  <span data-ttu-id="54d88-119">如果您已設定接收埠要求傳送者必須經過驗證、確實為系統中已知的合作對象，而 BizTalk Server 卻無法找到訊息傳送者的 PID，則 BizTalk Server 會依接收埠的組態而定，卸除或擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="54d88-119">If you configured the receiving port to require the sender to be authenticated to a known party in the system, and BizTalk Server is not able to find a PID for the sender of the message, then BizTalk Server drops or suspends the message depending on the configuration of the receive port.</span></span> <span data-ttu-id="54d88-120">BizTalk Server 提供這項功能來減輕「拒絕服務」攻擊的威脅。</span><span class="sxs-lookup"><span data-stu-id="54d88-120">BizTalk Server provides this feature to mitigate Denial of Service attacks.</span></span> <span data-ttu-id="54d88-121">如需接收埠的驗證選項的詳細資訊，請參閱[如何設定接收埠的驗證選項](../core/how-to-configure-authentication-options-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-121">For more information about the authentication options for receive ports, see [How to Configure Authentication Options for a Receive Port](../core/how-to-configure-authentication-options-for-a-receive-port.md).</span></span>  
  
3.  <span data-ttu-id="54d88-122">管線驗證訊息之後，會傳送訊息至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="54d88-122">After the pipeline authenticates the message, it sends the message to the MessageBox database.</span></span>  
  
    1.  <span data-ttu-id="54d88-123">如果加入佇列的主控件 (管線執行所在的主控件) 無法識別為驗證信任的主控件，則 MessageBox 資料庫會以 Guest 識別碼覆寫 PID，而以加入佇列的主控件執行個體執行時所用的服務帳戶來覆寫 SSID。</span><span class="sxs-lookup"><span data-stu-id="54d88-123">If you did not identify the enqueuing host (on which the pipeline is running) as an authentication trusted host, the MessageBox database overwrites the PID with the guest ID, and the SSID with the service account that the enqueuing host instance is running as.</span></span> <span data-ttu-id="54d88-124">如需驗證信任的主控件的詳細資訊，請參閱[驗證的訊息之間的處理序](../core/authentication-of-messages-between-processes.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-124">For more information about authentication trusted host, see [Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md).</span></span> <span data-ttu-id="54d88-125">如需如何設定驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-125">For more information about how to configure authentication trusted host, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
    2.  <span data-ttu-id="54d88-126">如果管線執行所在的主控件標示為信任的驗證，則 MessageBox 資料庫將信任 PID 和 SSID，並在訊息的內容中留下這個資訊，如此下游程序就可以使用這個資訊來對訊息的原始傳送者進行驗證和/或授權。</span><span class="sxs-lookup"><span data-stu-id="54d88-126">If the host on which the pipeline is running is marked as authentication trusted, the MessageBox database trusts the PID and SSID, and leaves this information in the context of the message so that downstream processes can use this information to authenticate and/or authorize the original sender of the message.</span></span>  
  
    3.  <span data-ttu-id="54d88-127">如果 BizTalk Server 必須有接收授權，則 MessageBox 資料庫會確認訂閱訊息的主控件是否有權接收訊息。</span><span class="sxs-lookup"><span data-stu-id="54d88-127">If BizTalk Server requires receive authorization, the MessageBox database verifies that the hosts subscribed to the message have authorization to receive it.</span></span> <span data-ttu-id="54d88-128">如需有關接收授權，請參閱[授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)。</span><span class="sxs-lookup"><span data-stu-id="54d88-128">For more information about receive authorization, see [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md).</span></span>  
  
4.  <span data-ttu-id="54d88-129">BizTalk Server 處理訊息之後，輸出管線會在編碼階段中對訊息進行加密和/或數位簽署。</span><span class="sxs-lookup"><span data-stu-id="54d88-129">After BizTalk Server processes the message, the outbound pipeline encrypts and/or digitally signs the message in the encode stage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d88-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d88-130">See Also</span></span>  
 <span data-ttu-id="54d88-131">[實作訊息安全性](../core/implementing-message-security.md) </span><span class="sxs-lookup"><span data-stu-id="54d88-131">[Implementing Message Security](../core/implementing-message-security.md) </span></span>  
 [<span data-ttu-id="54d88-132">規劃訊息安全性</span><span class="sxs-lookup"><span data-stu-id="54d88-132">Planning Message Security</span></span>](../core/planning-message-security.md)