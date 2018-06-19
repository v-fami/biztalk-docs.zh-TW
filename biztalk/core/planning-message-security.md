---
title: 規劃訊息安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- planning, security
- security, messages
- security, planning
- messages, security
ms.assetid: c0f93515-a822-425c-9155-270a179d6b61
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826db8480d378342ee30993f67bbd60e27751d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264286"
---
# <a name="planning-message-security"></a><span data-ttu-id="8f855-102">規劃訊息安全性</span><span class="sxs-lookup"><span data-stu-id="8f855-102">Planning Message Security</span></span>
<span data-ttu-id="8f855-103">基於貴公司的安全性原則，您可能需要考慮下表的問題來決定您必須在 BizTalk Server 環境中實作的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="8f855-103">Based on the security policies in your company, you may want to consider the questions in the following table to determine the level of security that you must implement in your BizTalk Server environment.</span></span> <span data-ttu-id="8f855-104">這些問題的答案將會決定傳訊所需的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="8f855-104">The answers to these questions will determine the security features that you need for messaging.</span></span>  
  
|<span data-ttu-id="8f855-105">問題</span><span class="sxs-lookup"><span data-stu-id="8f855-105">Question</span></span>|<span data-ttu-id="8f855-106">BizTalk Server 安全性功能</span><span class="sxs-lookup"><span data-stu-id="8f855-106">BizTalk Server Security Feature</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="8f855-107">**當接收訊息：**</span><span class="sxs-lookup"><span data-stu-id="8f855-107">**When receiving a message:**</span></span>||  
|<span data-ttu-id="8f855-108">您如何判定訊息傳送者的識別？</span><span class="sxs-lookup"><span data-stu-id="8f855-108">How do you determine the identity of the sender of the message?</span></span>|<span data-ttu-id="8f855-109">您可以使用 BizTalk 管線中的合作對象解析元件以及簽章憑證或 Windows 安全性識別碼 (SID)，來確認訊息的傳送者。</span><span class="sxs-lookup"><span data-stu-id="8f855-109">You can use the party resolution component in the BizTalk pipeline and the signing certificate or Windows Security ID (SID) to identify the sender of a message positively.</span></span> <span data-ttu-id="8f855-110">如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="8f855-110">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="8f855-111">是否知道傳送訊息給您的合作對象？</span><span class="sxs-lookup"><span data-stu-id="8f855-111">Do you know the party that sent you the message?</span></span>|<span data-ttu-id="8f855-112">您可以使用 BizTalk 管線中的合作對象解析元件，來判斷傳送訊息給您的合作對象是否為系統中既有的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="8f855-112">You can use the party resolution component in the BizTalk pipeline to determine whether the party that sent you the message is a trading partner already in your system.</span></span> <span data-ttu-id="8f855-113">如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="8f855-113">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="8f855-114">是否要避免從不認識的合作對象接收訊息？</span><span class="sxs-lookup"><span data-stu-id="8f855-114">Do you want to avoid receiving messages from parties you do not know?</span></span>|<span data-ttu-id="8f855-115">您可以在連接埠中使用 [需要驗證] 功能，以要求 BizTalk Server 僅處理來自認識的合作對象的訊息。</span><span class="sxs-lookup"><span data-stu-id="8f855-115">You can use the authentication required feature in the port to require that BizTalk server processes only the messages from parties that you know.</span></span> <span data-ttu-id="8f855-116">如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="8f855-116">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="8f855-117">**當傳送訊息：**</span><span class="sxs-lookup"><span data-stu-id="8f855-117">**When sending a message:**</span></span>||  
|<span data-ttu-id="8f855-118">您如何確保外寄訊息的私密性？</span><span class="sxs-lookup"><span data-stu-id="8f855-118">How do you ensure the privacy of outgoing messages?</span></span>|<span data-ttu-id="8f855-119">您可以加密訊息來確保只有預定的合作對象才能讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="8f855-119">You can encrypt the message to ensure that only the intended party can read the message.</span></span> <span data-ttu-id="8f855-120">如需詳細資訊，請參閱[輸出訊息保護](../core/outbound-message-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="8f855-120">For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).</span></span>|  
|<span data-ttu-id="8f855-121">如何防止惡意的使用者在傳輸期間竄改訊息？</span><span class="sxs-lookup"><span data-stu-id="8f855-121">How do you prevent malicious users from tampering with the message during transmission?</span></span>|<span data-ttu-id="8f855-122">您可以使用數位簽章來確保訊息的完整性。</span><span class="sxs-lookup"><span data-stu-id="8f855-122">You can use digital signatures to ensure the integrity of the message.</span></span> <span data-ttu-id="8f855-123">如需詳細資訊，請參閱[輸出訊息保護](../core/outbound-message-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="8f855-123">For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="8f855-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="8f855-124">In This Section</span></span>  
  
-   [<span data-ttu-id="8f855-125">傳送和接收訊息的安全性</span><span class="sxs-lookup"><span data-stu-id="8f855-125">Security for Sending and Receiving Messages</span></span>](../core/security-for-sending-and-receiving-messages.md)  
  
-   [<span data-ttu-id="8f855-126">加密和簽章憑證</span><span class="sxs-lookup"><span data-stu-id="8f855-126">Encryption and Signing Certificates</span></span>](../core/encryption-and-signing-certificates.md)  
  
-   [<span data-ttu-id="8f855-127">驗證訊息的寄件者</span><span class="sxs-lookup"><span data-stu-id="8f855-127">Authenticating the Sender of a Message</span></span>](../core/authenticating-the-sender-of-a-message.md)  
  
-   [<span data-ttu-id="8f855-128">授權訊息接收器</span><span class="sxs-lookup"><span data-stu-id="8f855-128">Authorizing the Receiver of a Message</span></span>](../core/authorizing-the-receiver-of-a-message.md)