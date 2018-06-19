---
title: 驗證訊息的傳送者 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parties, authenticating
- authenticating, authentication required
- messages, authenticating
- security, authenticating
- digital signatures, authenticating
- security, messages
- MessageBox database, authenticating
- authenticating, authentication trust
- messages, message flow
- authenticating, security
- authenticating, party resolution
- authenticating, digital signatures
- authenticating, messages
ms.assetid: 813a2fb9-0346-4129-9cc5-1713f72a491e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86bc83238d9cdfb435bd26264891ff699cbc3b48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232006"
---
# <a name="authenticating-the-sender-of-a-message"></a><span data-ttu-id="c8b4f-102">驗證訊息的寄件者</span><span class="sxs-lookup"><span data-stu-id="c8b4f-102">Authenticating the Sender of a Message</span></span>
<span data-ttu-id="c8b4f-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用各種不同機制來確認合作對象確實是其所自稱的身分，或處理程序確實是其所自稱的處理程序。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses different mechanisms to verify that a party is who they claim to be, or that a process is what it claims to be.</span></span> <span data-ttu-id="c8b4f-104">此外，您可以指定程序是否能轉送到本身是訊息原始傳送者的 BizTalk Server，以及 BizTalk Server 是否應將合作對象辨識為夥伴。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-104">Furthermore, you can specify whether the process can relay to BizTalk Server who the original sender of the message is, and whether BizTalk Server recognizes the party as a partner.</span></span>  
  
 <span data-ttu-id="c8b4f-105">下圖顯示可讓您對訊息傳送者進行驗證與授權的 BizTalk Server 中的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-105">The following figure shows the security features in BizTalk Server that enable you to authenticate and authorize the sender of a message.</span></span>  
  
 <span data-ttu-id="c8b4f-106">![安全訊息的安全性功能](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span><span class="sxs-lookup"><span data-stu-id="c8b4f-106">![Security features for secure messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span></span>  
<span data-ttu-id="c8b4f-107">BizTalk Server 用來驗證及授權訊息傳送者的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-107">The security features that BizTalk Server uses to authenticate and authorize the send of a message</span></span>  
  
 <span data-ttu-id="c8b4f-108">可讓您驗證訊息傳送者的功能為：</span><span class="sxs-lookup"><span data-stu-id="c8b4f-108">The features that enable you to authenticate the sender of a message are:</span></span>  
  
-   <span data-ttu-id="c8b4f-109">**數位簽章驗證。**</span><span class="sxs-lookup"><span data-stu-id="c8b4f-109">**Digital Signature Validation.**</span></span> <span data-ttu-id="c8b4f-110">如果訊息具有數位簽章，BizTalk Server 就會將它用來驗證傳送者的識別。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-110">If the message has a digital signature, BizTalk Server uses it to verify the identity of the sender.</span></span> <span data-ttu-id="c8b4f-111">如需如何設定數位簽章驗證的詳細資訊，請參閱[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-111">For more information about how to configure digital signature validation, see [How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).</span></span>  
  
-   <span data-ttu-id="c8b4f-112">**合作對象解析。**</span><span class="sxs-lookup"><span data-stu-id="c8b4f-112">**Party Resolution.**</span></span> <span data-ttu-id="c8b4f-113">插入 MessageBox 資料庫中的所有訊息 (不論其源自 BizTalk Server 內部或外部) 都帶有透過將數位憑證或 Windows 帳戶對應到 PID 的作法所決定的合作對象識別碼 (PID)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-113">All messages inserted into the MessageBox database, whether originating inside or outside of BizTalk Server, carry a Party ID (PID) that is determined through either the mapping of a digital certificate or a Windows Account to a PID.</span></span> <span data-ttu-id="c8b4f-114">如需如何設定合作對象解析元件的詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-114">For more information about how to configure party resolution component, see [Using Certificates for Party Resolution](../core/using-certificates-for-party-resolution.md).</span></span>  
  
-   <span data-ttu-id="c8b4f-115">**需要驗證。**</span><span class="sxs-lookup"><span data-stu-id="c8b4f-115">**Authentication required.**</span></span> <span data-ttu-id="c8b4f-116">如果接收埠無法判定訊息傳送者，BizTalk 主控件則可能將其當做「Guest」訊息接受，或完全不予理會。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-116">If the receive port is not able to determine the sender of the message, a BizTalk Host can either accept it as a "guest" message, or disregard it altogether.</span></span> <span data-ttu-id="c8b4f-117">這項功能可讓您保護系統不受「拒絕服務」攻擊的威脅，因為「追蹤」資料庫將不會處理或儲存來自未知合作對象的訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-117">This feature enables you to protect your system from Denial of Service attacks, as messages from unknown parties will not be processed or stored in the tracking database.</span></span> <span data-ttu-id="c8b4f-118">如需接收埠的驗證選項的詳細資訊，請參閱[如何設定接收埠的驗證選項](../core/how-to-configure-authentication-options-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-118">For more information about the authentication options for receive ports, see [How to Configure Authentication Options for a Receive Port](../core/how-to-configure-authentication-options-for-a-receive-port.md).</span></span>  
  
-   <span data-ttu-id="c8b4f-119">**驗證信任。**</span><span class="sxs-lookup"><span data-stu-id="c8b4f-119">**Authentication Trust.**</span></span> <span data-ttu-id="c8b4f-120">如果 MessageBox 資料庫從無法識別為驗證信任的主控件收到訊息，MessageBox 資料庫將會以 Guest 識別碼覆寫 PID，而以主控件執行個體執行所用的服務帳戶來覆寫 SSID。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-120">If the MessageBox database receives a message from a host that you did not identify as authentication trusted, the MessageBox database will overwrite the PID with the guest ID, and the SSID with the service account that the host instance is running as.</span></span> <span data-ttu-id="c8b4f-121">BizTalk Server 可讓識別為驗證信任的主控件指出信任的主控件佇列至 MessageBox 資料庫的訊息傳送者為實體，而不是信任的主控件本身。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-121">BizTalk Server enables hosts identified as authentication trusted to indicate that the sender of a message that the trusted host is queuing to the MessageBox database is an entity other than the trusted host itself.</span></span> <span data-ttu-id="c8b4f-122">「驗證信任」的主要目的是要讓管線可以解析成 PID，然後再將該 PID 一併傳遞到目前耗用的服務以供授權和輸出合作對象解析之用，以及允許將傳送者的 Windows 安全性識別碼 (SSID) 一併傳輸到目前耗用的服務以供協調流程動作授權之用。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-122">The primary purposes of authentication trust are to enable pipelines to resolve to a PID and pass that PID along to consuming services for use in authorization and outbound party resolution, and to enable the transmission of the sender Windows Security ID (SSID) along to consuming services for use in orchestration action authorization.</span></span> <span data-ttu-id="c8b4f-123">如需驗證信任的主控件的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-123">For more information about authentication trusted host, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span> <span data-ttu-id="c8b4f-124">如需如何使用 BizTalk Server 協調流程與合作對象解析的詳細資訊，請參閱[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-124">For more information about how to use BizTalk Server orchestrations in conjunction with party resolution, see [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).</span></span>  
  
 <span data-ttu-id="c8b4f-125">您可以依是否需要知道訊息傳送者、訊息原始傳送者或收件者或訊息檢視者而定，使用圖中顯示的部分或所有功能。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-125">Depending upon whether you need to know from whom you received this message, the original sender of the message, or the recipient or viewer of your message, you can use some or all of the features shown in the figure.</span></span>  
  
 <span data-ttu-id="c8b4f-126">如果「讓夥伴確知訊息來自於您，而且其他人無法在傳輸過程中讀取這些訊息」非常重要，您應該考慮使用下列技術，協助確保只有指定的收件者和收件者應用程式才可以接收訊息：</span><span class="sxs-lookup"><span data-stu-id="c8b4f-126">If it is important for your partners to know with certainty that messages are from you and that nobody else can read them while they are in transit, you should consider using the following techniques to help ensure that only the specified recipients and recipient applications receive the messages:</span></span>  
  
-   <span data-ttu-id="c8b4f-127">在輸出訊息中使用數位簽章，這樣您的夥伴就可以確認您是訊息傳送者。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-127">Use digital signatures for outbound messages so that your partner can verify that you are the sender of the message.</span></span>  
  
-   <span data-ttu-id="c8b4f-128">加密輸出訊息，協助確保未經授權的合作對象無法在傳輸過程中檢視訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-128">Encrypt outbound messages to help ensure that unauthorized parties cannot view the message while it is in transit.</span></span>  
  
 <span data-ttu-id="c8b4f-129">如果「判斷是誰將訊息傳送給貴公司，而且其他人無法在傳輸過程中讀取該訊息」非常重要，您應該考慮使用下列技術，協助確保只有指定的收件者和收件者應用程式才可以接收訊息：</span><span class="sxs-lookup"><span data-stu-id="c8b4f-129">If it is important to determine who sent your company a message and that nobody else read it while it was in transit, you should consider using the following techniques to help ensure that only the specified recipients and recipient applications receive the messages:</span></span>  
  
-   <span data-ttu-id="c8b4f-130">確定 BizTalk Server 只接受包含數位簽章的訊息，這樣您就知道是誰傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-130">Make sure BizTalk Server only accepts messages with digital signatures so that you know who sent the message.</span></span>  
  
-   <span data-ttu-id="c8b4f-131">確定您已將用來加密由夥伴傳送至 BizTalk Server 之訊息的公開金鑰憑證傳送給夥伴。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-131">Make sure you send your partners the public key certificate for encrypting the messages they send to BizTalk Server.</span></span> <span data-ttu-id="c8b4f-132">藉由使用加密，您可以協助確保未經授權的合作對象無法在傳輸過程中檢視訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-132">By using encryption, you can help ensure that unauthorized parties cannot view the message while it is in transit.</span></span>  
  
-   <span data-ttu-id="c8b4f-133">在接收埠中使用 [需要驗證] 屬性，以確定訊息是來自已知的合作對象。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-133">Use the authentication required property in the receive port to ensure the message is from a known party.</span></span>  
  
 <span data-ttu-id="c8b4f-134">經過一個以上的主控件處理訊息之後，您可能就會搞不清楚誰是訊息的原始傳送者。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-134">After more than one host processes the message, it may not be clear who the original sender of the message is.</span></span> <span data-ttu-id="c8b4f-135">為了避免在必須知道原始傳送者的識別時 (例如，授與存取權以傳送或接收訊息時) 發生上述情形，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供了可通過許多主控件來傳播原始傳送者識別的安全性機制，以便根據該識別驗證下游主控件的存取權。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-135">In cases where you must know the identity of the original sender, for example, when granting access to send or receive a message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a security mechanism for propagating the identity of the original sender through many hosts in order to validate access to downstream hosts based on that identity.</span></span> <span data-ttu-id="c8b4f-136">在 BizTalk Server 中，這個機制稱為「程序驗證信任」。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-136">In BizTalk Server, this calls process Authentication trust.</span></span> <span data-ttu-id="c8b4f-137">如需詳細資訊，請參閱[驗證的訊息之間的處理序](../core/authentication-of-messages-between-processes.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b4f-137">For more information, see [Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8b4f-138">本節內容</span><span class="sxs-lookup"><span data-stu-id="c8b4f-138">In This Section</span></span>  
  
-   [<span data-ttu-id="c8b4f-139">輸入訊息驗證</span><span class="sxs-lookup"><span data-stu-id="c8b4f-139">Inbound Message Authentication</span></span>](../core/inbound-message-authentication.md)  
  
-   [<span data-ttu-id="c8b4f-140">驗證的處理序之間的訊息</span><span class="sxs-lookup"><span data-stu-id="c8b4f-140">Authentication of Messages Between Processes</span></span>](../core/authentication-of-messages-between-processes.md)  
  
-   [<span data-ttu-id="c8b4f-141">輸出訊息保護</span><span class="sxs-lookup"><span data-stu-id="c8b4f-141">Outbound Message Protection</span></span>](../core/outbound-message-protection.md)