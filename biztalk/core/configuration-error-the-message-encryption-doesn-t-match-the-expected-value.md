---
title: 組態錯誤。 訊息加密不&#39;t 符合預期值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b08ace29bd4cee6cd5057cdb2b18fd1956b536
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976143"
---
# <a name="configuration-error-the-message-encryption-doesn39t-match-the-expected-value"></a><span data-ttu-id="5e523-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e523-103">Configuration error.</span></span> <span data-ttu-id="5e523-104">訊息加密不&#39;t 符合預期值</span><span class="sxs-lookup"><span data-stu-id="5e523-104">The message encryption doesn&#39;t match the expected value</span></span>
## <a name="details"></a><span data-ttu-id="5e523-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5e523-105">Details</span></span>  
  
|                 |                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5e523-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5e523-106">Product Name</span></span>   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                |
| <span data-ttu-id="5e523-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="5e523-107">Product Version</span></span> |                                                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                            |
|    <span data-ttu-id="5e523-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5e523-108">Event ID</span></span>     |                                                                                        -                                                                                         |
|  <span data-ttu-id="5e523-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5e523-109">Event Source</span></span>   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5e523-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="5e523-110"> EDI</span></span>                                              |
|    <span data-ttu-id="5e523-111">元件</span><span class="sxs-lookup"><span data-stu-id="5e523-111">Component</span></span>    |                                                                                    <span data-ttu-id="5e523-112">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="5e523-112">AS2 Engine</span></span>                                                                                    |
|  <span data-ttu-id="5e523-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5e523-113">Symbolic Name</span></span>  |                                                                   <span data-ttu-id="5e523-114">AS2DecoderPartyEncryptionConfigurationError</span><span class="sxs-lookup"><span data-stu-id="5e523-114">AS2DecoderPartyEncryptionConfigurationError</span></span>                                                                    |
|  <span data-ttu-id="5e523-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5e523-115">Message Text</span></span>   | <span data-ttu-id="5e523-116">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e523-116">Configuration error.</span></span> <span data-ttu-id="5e523-117">訊息加密不符合預期值。</span><span class="sxs-lookup"><span data-stu-id="5e523-117">The message encryption doesn't match the expected value.</span></span> <span data-ttu-id="5e523-118">請連絡傳送方夥伴，並確認加密用法。</span><span class="sxs-lookup"><span data-stu-id="5e523-118">Contact the sending partner and verify encryption use.</span></span> <span data-ttu-id="5e523-119">AS2-從:"{0}"AS2-到: 「{1}"MessageID:"{2}」</span><span class="sxs-lookup"><span data-stu-id="5e523-119">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="5e523-120">說明</span><span class="sxs-lookup"><span data-stu-id="5e523-120">Explanation</span></span>  
 <span data-ttu-id="5e523-121">這個錯誤/警告/資訊事件表示，由於已在合作對象設定中指定加密，但 AS2 訊息未經過加密，亦或是加密已指定為不啟用，但訊息已經過加密，因此接收管線的 AS2 解碼器元件無法處理 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="5e523-121">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because encryption is specified in the party settings, but the AS2 message is not encrypted, or encryption is specified not to be enabled, but the message is encrypted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e523-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5e523-122">User Action</span></span>  
 <span data-ttu-id="5e523-123">若要解決這個錯誤，請確認加密內送 AS2 訊息，是否在合作對象設定中指定加密，或如果指定了加密，未加密內送 AS2 訊息為未啟用合作對象設定中。</span><span class="sxs-lookup"><span data-stu-id="5e523-123">To resolve this error, verify that the incoming AS2 message is encrypted if encryption is specified in the party settings or that the incoming AS2 message is not encrypted if encryption is specified as not enabled in the party settings.</span></span> <span data-ttu-id="5e523-124">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="5e523-124">Do one of the following:</span></span>  
  
1.  <span data-ttu-id="5e523-125">如果**覆寫輸入的訊息屬性 屬性選取**的合作對象當做 AS2 訊息傳送者頁面的 AS2 屬性 對話方塊中，在 BizTalk Server 管理主控台中，**訊息應該加密**選取屬性，但是訊息並未加密，請連絡傳送訊息的合作對象並要求他們要加密訊息，並重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="5e523-125">If the **Override inbound message properties property is selected** in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be encrypted** property is selected, but the message is not encrypted, contact the party that sent the message and ask them to encrypt the message, and resend it.</span></span> <span data-ttu-id="5e523-126">或您可以清除**訊息應該加密**屬性，或有**覆寫輸入的訊息屬性**屬性。</span><span class="sxs-lookup"><span data-stu-id="5e523-126">Or you can clear the **Message should be encrypted** property, or the **Override inbound message properties** property.</span></span>  
  
2.  <span data-ttu-id="5e523-127">如果**覆寫輸入的訊息屬性**選取屬性，**訊息應該加密**清除屬性，但訊息已加密，請連絡傳送訊息的合作對象，並要求他們不加密訊息，並重新傳送它。</span><span class="sxs-lookup"><span data-stu-id="5e523-127">If the **Override inbound message properties** property is selected, the **Message should be encrypted** property is cleared, but the message is encrypted, contact the party that sent the message and ask them not to encrypt the message, and resend it.</span></span> <span data-ttu-id="5e523-128">或者您可以選取**訊息應該加密**屬性。</span><span class="sxs-lookup"><span data-stu-id="5e523-128">Or you can select the **Message should be encrypted** property.</span></span>