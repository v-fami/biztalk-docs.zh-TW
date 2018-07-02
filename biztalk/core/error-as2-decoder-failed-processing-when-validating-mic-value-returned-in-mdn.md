---
title: AS2 解碼器處理驗證 MDN 中傳回的 MIC 值時失敗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fe2d76d-b0f1-4118-8483-547c2c9fffb7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b15ec1518e4736052e31254283db66395d87fb6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985839"
---
# <a name="the-as2-decoder-failed-processing-when-validating-the-mic-value-returned-in-the-mdn"></a><span data-ttu-id="fd5e5-102">驗證 MDN 中傳回的 MIC 值時，AS2 解碼器處理失敗</span><span class="sxs-lookup"><span data-stu-id="fd5e5-102">The AS2 Decoder failed processing when validating the MIC value returned in the MDN</span></span>
## <a name="details"></a><span data-ttu-id="fd5e5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd5e5-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="fd5e5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fd5e5-104">Product Name</span></span>   |                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| <span data-ttu-id="fd5e5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fd5e5-105">Product Version</span></span> |                                                                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                       |
|    <span data-ttu-id="fd5e5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fd5e5-106">Event ID</span></span>     |                                                                                                   -                                                                                                   |
|  <span data-ttu-id="fd5e5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="fd5e5-107">Event Source</span></span>   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fd5e5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="fd5e5-108"> EDI</span></span>                                                         |
|    <span data-ttu-id="fd5e5-109">元件</span><span class="sxs-lookup"><span data-stu-id="fd5e5-109">Component</span></span>    |                                                                                              <span data-ttu-id="fd5e5-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="fd5e5-110">AS2 Engine</span></span>                                                                                               |
|  <span data-ttu-id="fd5e5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fd5e5-111">Symbolic Name</span></span>  |                                                                                <span data-ttu-id="fd5e5-112">AS2DecoderMdnMicFailureDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="fd5e5-112">AS2DecoderMdnMicFailureDuringProcessing</span></span>                                                                                |
|  <span data-ttu-id="fd5e5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fd5e5-113">Message Text</span></span>   | <span data-ttu-id="fd5e5-114">驗證 MDN 中傳回的 MIC 值時，AS2 解碼器處理失敗。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-114">The AS2 Decoder failed processing when validating the MIC value returned in the MDN.</span></span>  <span data-ttu-id="fd5e5-115">MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"{1}"MessageID:"{2}"OriginalMessageID:"{3}」</span><span class="sxs-lookup"><span data-stu-id="fd5e5-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="fd5e5-116">說明</span><span class="sxs-lookup"><span data-stu-id="fd5e5-116">Explanation</span></span>  
 <span data-ttu-id="fd5e5-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送 MDN 的 MIC （訊息完整性檢查） 驗證失敗。 因為。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN because the MIC (Message Integrity Check) failed validation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fd5e5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fd5e5-118">User Action</span></span>  
 <span data-ttu-id="fd5e5-119">若要解決這個錯誤，請確認用來產生 MDN （在原始訊息的簽章-回條-MICalg 標頭） 的演算法是做為 AS2 訊息接收者的簽章-回條-MICalg 屬性中指定的演算法相同。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-119">To resolve this error, verify that the algorithm used for generating the MDN (in the Signed-Receipt-MICalg header of the original message) is the same as the algorithm specified in the Signed-Receipt-MICalg property for the AS2 Message Receiver.</span></span> <span data-ttu-id="fd5e5-120">兩者都應該是 SHA1 或 MD5。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-120">Both should be either SHA1 or MD5.</span></span> <span data-ttu-id="fd5e5-121">如果指定的演算法都相同，請確認已收到內容現場多部分簽署的 MDN 訊息的第二部分中的延伸模組欄位包含有效的 MIC 摘要。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-121">If the algorithm specified is the same, verify that Received-Content-MIC extension field in the second part of the multipart signed MDN message includes a valid MIC digest.</span></span> <span data-ttu-id="fd5e5-122">如果有的話，判斷為什麼 MDN 沒有對應至已傳送交換。</span><span class="sxs-lookup"><span data-stu-id="fd5e5-122">If it does, determine why the MDN does not correspond to the interchange that was sent.</span></span>