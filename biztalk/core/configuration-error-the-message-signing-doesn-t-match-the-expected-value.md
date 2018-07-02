---
title: 組態錯誤。 訊息簽章不&#39;t 符合預期的值。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f067351-b6b0-479d-b2ff-81e9f45b5924
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dfe2b610724a346ed31fb0951aa90c660f41d82
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975935"
---
# <a name="configuration-error-the-message-signing-doesn39t-match-the-expected-value"></a><span data-ttu-id="a2135-104">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2135-104">Configuration error.</span></span> <span data-ttu-id="a2135-105">訊息簽章不&#39;t 符合預期的值。</span><span class="sxs-lookup"><span data-stu-id="a2135-105">The message signing doesn&#39;t match the expected value.</span></span>
## <a name="details"></a><span data-ttu-id="a2135-106">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a2135-106">Details</span></span>  
  
|                 |                                                                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a2135-107">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a2135-107">Product Name</span></span>   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                              |
| <span data-ttu-id="a2135-108">產品版本</span><span class="sxs-lookup"><span data-stu-id="a2135-108">Product Version</span></span> |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                          |
|    <span data-ttu-id="a2135-109">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a2135-109">Event ID</span></span>     |                                                                                      -                                                                                       |
|  <span data-ttu-id="a2135-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="a2135-110">Event Source</span></span>   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a2135-111"> EDI</span><span class="sxs-lookup"><span data-stu-id="a2135-111"> EDI</span></span>                                            |
|    <span data-ttu-id="a2135-112">元件</span><span class="sxs-lookup"><span data-stu-id="a2135-112">Component</span></span>    |                                                                                  <span data-ttu-id="a2135-113">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="a2135-113">AS2 Engine</span></span>                                                                                  |
|  <span data-ttu-id="a2135-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a2135-114">Symbolic Name</span></span>  |                                                                   <span data-ttu-id="a2135-115">AS2DecoderPartySigningConfigurationError</span><span class="sxs-lookup"><span data-stu-id="a2135-115">AS2DecoderPartySigningConfigurationError</span></span>                                                                   |
|  <span data-ttu-id="a2135-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a2135-116">Message Text</span></span>   | <span data-ttu-id="a2135-117">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2135-117">Configuration error.</span></span> <span data-ttu-id="a2135-118">訊息簽章不符合預期值。</span><span class="sxs-lookup"><span data-stu-id="a2135-118">The message signing doesn't match the expected value.</span></span> <span data-ttu-id="a2135-119">請連絡傳送方夥伴，並確認簽章用法。</span><span class="sxs-lookup"><span data-stu-id="a2135-119">Contact the sending partner and verify signature use.</span></span> <span data-ttu-id="a2135-120">AS2-從:"{0}"AS2-到: 「{1}"MessageID:"{2}」</span><span class="sxs-lookup"><span data-stu-id="a2135-120">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a2135-121">說明</span><span class="sxs-lookup"><span data-stu-id="a2135-121">Explanation</span></span>  
 <span data-ttu-id="a2135-122">這個錯誤/警告/資訊事件表示，接收管線的 AS2 解碼器元件無法處理 AS2 訊息因為簽章指定在合作對象設定中，但未簽署 AS2 訊息，或簽章指定為不啟用，但是，訊息簽章。</span><span class="sxs-lookup"><span data-stu-id="a2135-122">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because signing is specified in the party settings, but the AS2 message is not signed, or signing is specified not to be enabled, but the message is signed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a2135-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a2135-123">User Action</span></span>  
 <span data-ttu-id="a2135-124">若要解決這個錯誤，請確認內送的 AS2 訊息已簽署，如果簽章的合作對象設定中指定，或如果簽署，未簽署內送 AS2 訊息指未在合作對象設定中啟用。</span><span class="sxs-lookup"><span data-stu-id="a2135-124">To resolve this error, verify that the incoming AS2 message is signed if signing is specified in the party settings or that the incoming AS2 message is not signed if signing is specified as not enabled in the party settings.</span></span> <span data-ttu-id="a2135-125">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="a2135-125">Do one of the following:</span></span>  
  
1.  <span data-ttu-id="a2135-126">如果**覆寫輸入的訊息屬性**的合作對象當做 AS2 訊息傳送者頁面的 [AS2 屬性] 對話方塊中，在 BizTalk Server 管理主控台中，選取屬性**訊息應該簽署的**選取屬性，但不是簽署訊息，請連絡傳送訊息的合作對象並要求他們簽章訊息，並重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="a2135-126">If the **Override inbound message properties** property is selected in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be signed** property is selected, but the message is not signed, contact the party that sent the message and ask them to sign the message, and resend it.</span></span> <span data-ttu-id="a2135-127">或您可以清除**訊息應該簽署**屬性，或有**覆寫輸入的訊息屬性**屬性。</span><span class="sxs-lookup"><span data-stu-id="a2135-127">Or you can clear the **Message should be signed** property, or the **Override inbound message properties** property.</span></span>  
  
2.  <span data-ttu-id="a2135-128">如果**覆寫輸入的訊息屬性**選取屬性，**訊息應該簽署**清除屬性，但訊息已簽署，請連絡傳送訊息的合作對象並不要求他們簽署訊息，並重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="a2135-128">If the **Override inbound message properties** property is selected, the **Message should be signed** property is cleared, but the message is signed, contact the party that sent the message and ask them not to sign the message, and resend it.</span></span> <span data-ttu-id="a2135-129">或者您可以選取**訊息應該簽署**屬性。</span><span class="sxs-lookup"><span data-stu-id="a2135-129">Or you can select the **Message should be signed** property.</span></span>