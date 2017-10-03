---
title: "AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc0660a64ff0aeb35976ad1aa45a602d8db0913a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-signing-did-not-match-our-request"></a><span data-ttu-id="7b512-102">AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求</span><span class="sxs-lookup"><span data-stu-id="7b512-102">The AS2 Decoder failed processing because the MDN signing did not match our request</span></span>
## <a name="details"></a><span data-ttu-id="7b512-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b512-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b512-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7b512-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7b512-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7b512-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7b512-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7b512-106">Event ID</span></span>|-|  
|<span data-ttu-id="7b512-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="7b512-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7b512-108">EDI</span><span class="sxs-lookup"><span data-stu-id="7b512-108"> EDI</span></span>|  
|<span data-ttu-id="7b512-109">元件</span><span class="sxs-lookup"><span data-stu-id="7b512-109">Component</span></span>|<span data-ttu-id="7b512-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="7b512-110">AS2 Engine</span></span>|  
|<span data-ttu-id="7b512-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7b512-111">Symbolic Name</span></span>|<span data-ttu-id="7b512-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="7b512-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span></span>|  
|<span data-ttu-id="7b512-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7b512-113">Message Text</span></span>|<span data-ttu-id="7b512-114">AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求。</span><span class="sxs-lookup"><span data-stu-id="7b512-114">The AS2 Decoder failure processing because the MDN signing did not match our request.</span></span>  <span data-ttu-id="7b512-115">MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"</span><span class="sxs-lookup"><span data-stu-id="7b512-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7b512-116">說明</span><span class="sxs-lookup"><span data-stu-id="7b512-116">Explanation</span></span>  
 <span data-ttu-id="7b512-117">這個錯誤/警告/資訊事件表示接收管線無法處理內送 MDN 是因為在已簽署的 MDN，但簽章未要求 MDN 或將 MDN 是不帶正負號，但簽章要求 mdn。</span><span class="sxs-lookup"><span data-stu-id="7b512-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN either because the MDN was signed, but signing wasn't requested for the MDN, or the MDN was unsigned, but signing was requested for the MDN.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b512-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7b512-118">User Action</span></span>  
 <span data-ttu-id="7b512-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7b512-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="7b512-120">變更以符合要求 MDN 簽章要求。</span><span class="sxs-lookup"><span data-stu-id="7b512-120">Change the signature request for the MDN to match the request.</span></span> <span data-ttu-id="7b512-121">若要這樣做，請開啟合作對象當做 AS2 訊息接收者 頁面的 AS2 屬性 對話方塊中，與所選取的 要求 MDN 屬性，選取或清除 要求簽署的 MDN 屬性。</span><span class="sxs-lookup"><span data-stu-id="7b512-121">To do so, open the Party as AS2 Message Receiver page of the AS2 Properties dialog box, and with the "Request MDN" property selected, either select or clear the "Request signed MDN" property.</span></span>  
  
2.  <span data-ttu-id="7b512-122">若要解決與否，是否應該簽署 Mdn 原始 AS2 訊息接收者，請連絡。</span><span class="sxs-lookup"><span data-stu-id="7b512-122">Contact the receiver of the original AS2 message to resolve whether MDNs should be signed or not.</span></span>