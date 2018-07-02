---
title: AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a4d5cb5cd1825f5620ab39e4c770eb9818a5ade
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978868"
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-signing-did-not-match-our-request"></a><span data-ttu-id="88cd5-102">AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求</span><span class="sxs-lookup"><span data-stu-id="88cd5-102">The AS2 Decoder failed processing because the MDN signing did not match our request</span></span>
## <a name="details"></a><span data-ttu-id="88cd5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88cd5-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="88cd5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="88cd5-104">Product Name</span></span>   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| <span data-ttu-id="88cd5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="88cd5-105">Product Version</span></span> |                                                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                       |
|    <span data-ttu-id="88cd5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="88cd5-106">Event ID</span></span>     |                                                                                                   -                                                                                                    |
|  <span data-ttu-id="88cd5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="88cd5-107">Event Source</span></span>   |                                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="88cd5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="88cd5-108"> EDI</span></span>                                                         |
|    <span data-ttu-id="88cd5-109">元件</span><span class="sxs-lookup"><span data-stu-id="88cd5-109">Component</span></span>    |                                                                                               <span data-ttu-id="88cd5-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="88cd5-110">AS2 Engine</span></span>                                                                                               |
|  <span data-ttu-id="88cd5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="88cd5-111">Symbolic Name</span></span>  |                                                                          <span data-ttu-id="88cd5-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="88cd5-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span></span>                                                                           |
|  <span data-ttu-id="88cd5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="88cd5-113">Message Text</span></span>   | <span data-ttu-id="88cd5-114">AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求。</span><span class="sxs-lookup"><span data-stu-id="88cd5-114">The AS2 Decoder failure processing because the MDN signing did not match our request.</span></span>  <span data-ttu-id="88cd5-115">MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"{1}"MessageID:"{2}"OriginalMessageID:"{3}」</span><span class="sxs-lookup"><span data-stu-id="88cd5-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="88cd5-116">說明</span><span class="sxs-lookup"><span data-stu-id="88cd5-116">Explanation</span></span>  
 <span data-ttu-id="88cd5-117">這個錯誤/警告/資訊事件表示接收管線無法處理內送 MDN 是因為在已簽署 MDN，但簽章未要求 MDN 或將 MDN 是不帶正負號，但簽署要求的 MDN。</span><span class="sxs-lookup"><span data-stu-id="88cd5-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN either because the MDN was signed, but signing wasn't requested for the MDN, or the MDN was unsigned, but signing was requested for the MDN.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="88cd5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="88cd5-118">User Action</span></span>  
 <span data-ttu-id="88cd5-119">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="88cd5-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="88cd5-120">變更以符合 要求 MDN 的簽章要求。</span><span class="sxs-lookup"><span data-stu-id="88cd5-120">Change the signature request for the MDN to match the request.</span></span> <span data-ttu-id="88cd5-121">若要這樣做，開啟 合作對象當做 AS2 訊息接收者 頁面的 AS2 屬性 對話方塊中，與所選取的 「 要求 MDN 屬性，選取或清除 要求簽署 MDN 屬性。</span><span class="sxs-lookup"><span data-stu-id="88cd5-121">To do so, open the Party as AS2 Message Receiver page of the AS2 Properties dialog box, and with the "Request MDN" property selected, either select or clear the "Request signed MDN" property.</span></span>  
  
2.  <span data-ttu-id="88cd5-122">請連絡原始解決與否，是否應該簽署 Mdn 的 AS2 訊息接收者。</span><span class="sxs-lookup"><span data-stu-id="88cd5-122">Contact the receiver of the original AS2 message to resolve whether MDNs should be signed or not.</span></span>