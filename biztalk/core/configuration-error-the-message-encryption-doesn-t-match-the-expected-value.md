---
title: "組態錯誤。 訊息加密不 &#39; 符合預期的值 t |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4920a4c26cb60c3215f58297445dc49551b1befe
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuration-error-the-message-encryption-doesn39t-match-the-expected-value"></a><span data-ttu-id="7ba38-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ba38-103">Configuration error.</span></span> <span data-ttu-id="7ba38-104">訊息加密不 &#39; t 符合預期值</span><span class="sxs-lookup"><span data-stu-id="7ba38-104">The message encryption doesn&#39;t match the expected value</span></span>
## <a name="details"></a><span data-ttu-id="7ba38-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7ba38-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ba38-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7ba38-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7ba38-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="7ba38-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7ba38-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7ba38-108">Event ID</span></span>|-|  
|<span data-ttu-id="7ba38-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7ba38-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7ba38-110">EDI</span><span class="sxs-lookup"><span data-stu-id="7ba38-110"> EDI</span></span>|  
|<span data-ttu-id="7ba38-111">元件</span><span class="sxs-lookup"><span data-stu-id="7ba38-111">Component</span></span>|<span data-ttu-id="7ba38-112">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="7ba38-112">AS2 Engine</span></span>|  
|<span data-ttu-id="7ba38-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7ba38-113">Symbolic Name</span></span>|<span data-ttu-id="7ba38-114">AS2DecoderPartyEncryptionConfigurationError</span><span class="sxs-lookup"><span data-stu-id="7ba38-114">AS2DecoderPartyEncryptionConfigurationError</span></span>|  
|<span data-ttu-id="7ba38-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7ba38-115">Message Text</span></span>|<span data-ttu-id="7ba38-116">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ba38-116">Configuration error.</span></span> <span data-ttu-id="7ba38-117">訊息加密不符合預期值。</span><span class="sxs-lookup"><span data-stu-id="7ba38-117">The message encryption doesn't match the expected value.</span></span> <span data-ttu-id="7ba38-118">請連絡傳送方夥伴，並確認加密用法。</span><span class="sxs-lookup"><span data-stu-id="7ba38-118">Contact the sending partner and verify encryption use.</span></span> <span data-ttu-id="7ba38-119">AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"</span><span class="sxs-lookup"><span data-stu-id="7ba38-119">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ba38-120">說明</span><span class="sxs-lookup"><span data-stu-id="7ba38-120">Explanation</span></span>  
 <span data-ttu-id="7ba38-121">這個錯誤/警告/資訊事件表示，由於已在合作對象設定中指定加密，但 AS2 訊息未經過加密，亦或是加密已指定為不啟用，但訊息已經過加密，因此接收管線的 AS2 解碼器元件無法處理 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba38-121">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because encryption is specified in the party settings, but the AS2 message is not encrypted, or encryption is specified not to be enabled, but the message is encrypted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ba38-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7ba38-122">User Action</span></span>  
 <span data-ttu-id="7ba38-123">若要解決這個錯誤，請確認是否合作對象設定中指定加密或未加密內送 AS2 訊息如果指定加密則為未在設定中啟用合作對象，確定已加密內送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba38-123">To resolve this error, verify that the incoming AS2 message is encrypted if encryption is specified in the party settings or that the incoming AS2 message is not encrypted if encryption is specified as not enabled in the party settings.</span></span> <span data-ttu-id="7ba38-124">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="7ba38-124">Do one of the following:</span></span>  
  
1.  <span data-ttu-id="7ba38-125">如果**覆寫輸入的訊息屬性 屬性選取**的合作對象當做 AS2 訊息傳送者在 BizTalk Server 管理主控台中，AS2 屬性 對話方塊頁面**訊息應該加密**選取屬性，但是訊息並未加密，請連絡傳送訊息的合作對象並要求他們將訊息加密，，重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="7ba38-125">If the **Override inbound message properties property is selected** in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be encrypted** property is selected, but the message is not encrypted, contact the party that sent the message and ask them to encrypt the message, and resend it.</span></span> <span data-ttu-id="7ba38-126">您可以清除或**訊息應該加密**屬性，或**覆寫輸入的訊息屬性**屬性。</span><span class="sxs-lookup"><span data-stu-id="7ba38-126">Or you can clear the **Message should be encrypted** property, or the **Override inbound message properties** property.</span></span>  
  
2.  <span data-ttu-id="7ba38-127">如果**覆寫輸入的訊息屬性**選取屬性，**訊息應該加密**清除屬性，但訊息經過加密，請連絡傳送訊息的合作對象，要求他們未以加密訊息，並重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="7ba38-127">If the **Override inbound message properties** property is selected, the **Message should be encrypted** property is cleared, but the message is encrypted, contact the party that sent the message and ask them not to encrypt the message, and resend it.</span></span> <span data-ttu-id="7ba38-128">您可以選取或**訊息應該加密**屬性。</span><span class="sxs-lookup"><span data-stu-id="7ba38-128">Or you can select the **Message should be encrypted** property.</span></span>