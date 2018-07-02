---
title: 組態錯誤。 訊息簽章不&#39;t 符合此合作對象設定簽章 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cea0016-12e8-4ee8-ac44-11024b5e74ef
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 729fff283d8fa63ce9e933a0dc69a4a8f2200874
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980455"
---
# <a name="configuration-error-the-message-signature-doesn39t-match-the-signature-configured-for-this-party"></a><span data-ttu-id="489ec-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="489ec-103">Configuration error.</span></span> <span data-ttu-id="489ec-104">訊息簽章不&#39;t 符合此合作對象設定簽章</span><span class="sxs-lookup"><span data-stu-id="489ec-104">The message signature doesn&#39;t match the signature configured for this party</span></span>
## <a name="details"></a><span data-ttu-id="489ec-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="489ec-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="489ec-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="489ec-106">Product Name</span></span>   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| <span data-ttu-id="489ec-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="489ec-107">Product Version</span></span> |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    <span data-ttu-id="489ec-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="489ec-108">Event ID</span></span>     |                                                                                                     -                                                                                                      |
|  <span data-ttu-id="489ec-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="489ec-109">Event Source</span></span>   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="489ec-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="489ec-110"> EDI</span></span>                                                           |
|    <span data-ttu-id="489ec-111">元件</span><span class="sxs-lookup"><span data-stu-id="489ec-111">Component</span></span>    |                                                                                                 <span data-ttu-id="489ec-112">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="489ec-112">AS2 Engine</span></span>                                                                                                 |
|  <span data-ttu-id="489ec-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="489ec-113">Symbolic Name</span></span>  |                                                                                                     -                                                                                                      |
|  <span data-ttu-id="489ec-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="489ec-114">Message Text</span></span>   | <span data-ttu-id="489ec-115">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="489ec-115">Configuration error.</span></span> <span data-ttu-id="489ec-116">訊息簽章不符合此合作對象的設定簽章。</span><span class="sxs-lookup"><span data-stu-id="489ec-116">The message signature doesn't match the signature configured for this party.</span></span> <span data-ttu-id="489ec-117">請連絡傳送方夥伴，並確認所用的憑證。</span><span class="sxs-lookup"><span data-stu-id="489ec-117">Contact the sending partner and verify the certificate used.</span></span> <span data-ttu-id="489ec-118">AS2-從:"{0}"AS2-到: 「{1}"MessageID:"{2}」</span><span class="sxs-lookup"><span data-stu-id="489ec-118">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="489ec-119">說明</span><span class="sxs-lookup"><span data-stu-id="489ec-119">Explanation</span></span>  
 <span data-ttu-id="489ec-120">這個錯誤/警告/資訊事件表示，AS2 接收管線無法驗證簽章，執行 MIME 處理時。</span><span class="sxs-lookup"><span data-stu-id="489ec-120">This Error/Warning/Information event indicates that the AS2 receive pipeline could not verify the signature when performing MIME processing.</span></span> <span data-ttu-id="489ec-121">這會導致從使用不同的憑證來處理收到的訊息，比用來簽署訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="489ec-121">This could result from using a different certificate to process the received message than the sender used to sign the message.</span></span> <span data-ttu-id="489ec-122">如果 BizTalk Server 會使用錯誤的合作對象設定來驗證內送 AS2 訊息的簽章，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="489ec-122">This can occur if BizTalk Server uses the settings of the wrong party to verify the signature of the incoming AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="489ec-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="489ec-123">User Action</span></span>  
 <span data-ttu-id="489ec-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="489ec-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="489ec-125">請確定正確的合作對象由內送 AS2 訊息的合作對象解析程序。</span><span class="sxs-lookup"><span data-stu-id="489ec-125">Ensure that the correct party is determined by the party resolution process for the incoming AS2 message.</span></span> <span data-ttu-id="489ec-126">這樣做的驗證會解析正確的合作對象，當 BizTalk Server 會嘗試比對 AS2-From 標頭中的內送訊息和合作對象屬性 對話方塊的 一般 頁面中的 別名 清單中的 EDIINT-AS2 From 值。</span><span class="sxs-lookup"><span data-stu-id="489ec-126">Do so by verifying that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From header in the incoming message and the value for EDIINT-AS2 From in the Aliases list in the General page of the Party Properties dialog box.</span></span> <span data-ttu-id="489ec-127">如果這麼做無法解決合作對象，請確認正確的合作對象已解決，當 BizTalk Server 會嘗試比對 AS2-From 內容屬性設定為內送訊息和合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="489ec-127">If that does not resolve the party, verify that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From context property that is set for the incoming message and the name of a party.</span></span>  
  
-   <span data-ttu-id="489ec-128">請確定憑證中 [憑證] 頁面的 [合作對象屬性] 對話方塊中，定義並儲存在本機電腦 \ 其他人 」 存放區，對應至用來簽署訊息的憑證。</span><span class="sxs-lookup"><span data-stu-id="489ec-128">Ensure that the certificate defined in the Certificate page of the Party Properties dialog box, and stored in the Local computer\Other People store, corresponds to the certificate used to sign the message.</span></span>