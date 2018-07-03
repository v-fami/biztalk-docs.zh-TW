---
title: 授權訊息接收器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, messages
- messages, receive authorization
- receive authorization
- messages, security
ms.assetid: c0cdb3ef-ee8e-40a1-9362-13cd26495951
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 612aa7cfca75e34248a094113258fc3c261ef14e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997231"
---
# <a name="authorizing-the-receiver-of-a-message"></a><span data-ttu-id="6bd44-102">授權訊息接收器</span><span class="sxs-lookup"><span data-stu-id="6bd44-102">Authorizing the Receiver of a Message</span></span>
<span data-ttu-id="6bd44-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您限制您授權接收訊息的處理程序和合作對象。</span><span class="sxs-lookup"><span data-stu-id="6bd44-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to limit the processes and parties that you authorize to receive messages.</span></span>  
  
 <span data-ttu-id="6bd44-104">下圖顯示您用來授權訊息接收器的 BizTalk Server 中的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6bd44-104">The following figure shows the security features in BizTalk Server that you use to authorize the receiver of a message.</span></span>  
  
 <span data-ttu-id="6bd44-105">![授權訊息接收器的安全性功能](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")</span><span class="sxs-lookup"><span data-stu-id="6bd44-105">![Security features authorizing the message receiver](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")</span></span>  
<span data-ttu-id="6bd44-106">BizTalk Server 用來授權訊息接收器的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6bd44-106">Security features BizTalk Server uses to authorize the receiver of a message.</span></span>  
  
 <span data-ttu-id="6bd44-107">您可以使用下列安全性機制來建立具有接收您所傳送訊息的權限 (授權) 的使用者：</span><span class="sxs-lookup"><span data-stu-id="6bd44-107">You can use the following security mechanisms to establish who has permission (authorization) to receive the messages that you send:</span></span>  
  
-   <span data-ttu-id="6bd44-108">**解密。**</span><span class="sxs-lookup"><span data-stu-id="6bd44-108">**Decryption.**</span></span> <span data-ttu-id="6bd44-109">請確定傳送訊息至 BizTalk Server 的合作對象持有用來加密其傳送至 BizTalk Server 之訊息的公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="6bd44-109">Make sure the parties that send messages to BizTalk Server have the public key certificate for encrypting messages they send to BizTalk Server.</span></span> <span data-ttu-id="6bd44-110">BizTalk Server 使用私密金鑰憑證來解密訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-110">BizTalk Server uses the private key certificate to decrypt the message.</span></span>  
  
-   <span data-ttu-id="6bd44-111">**接收授權。**</span><span class="sxs-lookup"><span data-stu-id="6bd44-111">**Receive Authorization.**</span></span> <span data-ttu-id="6bd44-112">您可以使用這個方法來控制 BizTalk Server 環境內的哪些主控件可以接收指定訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-112">You can use this method to control which hosts within the BizTalk Server environment can receive a given message.</span></span>  
  
-   <span data-ttu-id="6bd44-113">**加密。**</span><span class="sxs-lookup"><span data-stu-id="6bd44-113">**Encryption.**</span></span> <span data-ttu-id="6bd44-114">在 BizTalk 加密訊息時使用來自指定合作對象的公開金鑰憑證，可以確保只有預定的合作對象才可以讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-114">By using the public key certificate from a given party when BizTalk encrypts a message, you can ensure that only the intended party is able to read the message.</span></span>  
  
## <a name="receive-authorization"></a><span data-ttu-id="6bd44-115">接收授權</span><span class="sxs-lookup"><span data-stu-id="6bd44-115">Receive Authorization</span></span>  
 <span data-ttu-id="6bd44-116">接收授權是可用來控制哪些主控件可以接收 (訂閱) 指定訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="6bd44-116">Receive authorization is the method you can use to control which hosts can receive (subscribe for) a given message.</span></span> <span data-ttu-id="6bd44-117">BizTalk Server 使用的憑證資訊，因為在訊息上的訂用帳戶的屬性，以符合述詞： MessageBox 資料庫只會標示為已主機，該訊息的解密憑證需要授權的訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-117">BizTalk Server uses the certificate information as a subscription property to match predicates on the message: the MessageBox database only routes messages marked as authorization required to the hosts that have the decryption certificate for that message.</span></span> <span data-ttu-id="6bd44-118">為了方便說明這個程序，請您考量下列實例：</span><span class="sxs-lookup"><span data-stu-id="6bd44-118">To illustrate the process, consider the following scenarios:</span></span>  
  
- <span data-ttu-id="6bd44-119">**路由傳送未加密的訊息：** 時 BizTalk Server 收到訊息寄件者未加密時，沒有關於 BizTalk 如何路由傳送訊息的解密限制。</span><span class="sxs-lookup"><span data-stu-id="6bd44-119">**Routing an un-encrypted message:** When BizTalk Server receives a message that the sender did not encrypt, there is no decryption limitation as to how BizTalk routes the message.</span></span> <span data-ttu-id="6bd44-120">不論主控件有無設定接收授權憑證，都可以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-120">Both hosts with and hosts without receive authorization certificates configured can receive the message.</span></span>  
  
- <span data-ttu-id="6bd44-121">**加密的訊息路由傳送：** 加密的訊息送達時，接收管線必須包含解密訊息的解碼元件。</span><span class="sxs-lookup"><span data-stu-id="6bd44-121">**Routing an encrypted message:** When an encrypted message arrives, the receiving pipeline must contain a decoding component that decrypts the message.</span></span> <span data-ttu-id="6bd44-122">當 BizTalk Server 在解密訊息後進行路由時，BizTalk 使用可用來解密訊息的憑證指紋做為 MessageBox 資料庫訂閱機制中的識別項，並且只有那些以該項憑證設定的主控件才能接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6bd44-122">When BizTalk Server routes a message after it is decrypted, BizTalk uses the certificate thumbprint used to decrypt the message as evidence in the MessageBox database subscription mechanism, and only those hosts configured with that certificate receive the message.</span></span>  
  
  <span data-ttu-id="6bd44-123">如果要使用接收授權，則必須在您想要授權其接收訊息之主控件的屬性中提供解密憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="6bd44-123">If you want to use receive authorization, you must provide the thumbprint of the decryption certificate in the properties of the host that you want to authorize to receive the message.</span></span> <span data-ttu-id="6bd44-124">如需接收授權，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd44-124">For more information about receive authorization, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd44-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd44-125">See Also</span></span>  
 <span data-ttu-id="6bd44-126">[輸入訊息驗證](../core/inbound-message-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="6bd44-126">[Inbound Message Authentication](../core/inbound-message-authentication.md) </span></span>  
 <span data-ttu-id="6bd44-127">[處理序之間的訊息驗證](../core/authentication-of-messages-between-processes.md) </span><span class="sxs-lookup"><span data-stu-id="6bd44-127">[Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md) </span></span>  
 <span data-ttu-id="6bd44-128">[輸出訊息保護](../core/outbound-message-protection.md) </span><span class="sxs-lookup"><span data-stu-id="6bd44-128">[Outbound Message Protection](../core/outbound-message-protection.md) </span></span>  
 <span data-ttu-id="6bd44-129">[驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="6bd44-129">[Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) </span></span>  
 [<span data-ttu-id="6bd44-130">規劃訊息安全性</span><span class="sxs-lookup"><span data-stu-id="6bd44-130">Planning Message Security</span></span>](../core/planning-message-security.md)