---
title: "設定接收埠內送 mdn |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d156beae-e145-48de-9f02-37457073ef97
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8585ae946e15d2677e225d42f6c123d5dd5e8e49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-a-receive-port-for-incoming-mdns"></a><span data-ttu-id="310be-102">設定內送 MDN 的接收埠</span><span class="sxs-lookup"><span data-stu-id="310be-102">Configuring a Receive Port for Incoming MDNs</span></span>
<span data-ttu-id="310be-103">若要接收 AS2 MDN，請針對接收此訊息並將回應傳回給合作對象的作業，建立單向 HTTP 接收埠。</span><span class="sxs-lookup"><span data-stu-id="310be-103">To receive an AS2 MDN, create a one-way HTTP receive port to receive the message and return a response back to the party.</span></span>  
  
 <span data-ttu-id="310be-104">用來接收 AS2 訊息的雙向要求-回應接收埠，不應用來接收 MDN 訊息。</span><span class="sxs-lookup"><span data-stu-id="310be-104">A two-way request-response receive port that is used to receive AS2 messages should not be used to receive MDN messages.</span></span> <span data-ttu-id="310be-105">針對 MDN 使用要求-回應接收埠，將導致 200OK 訊息無法在回應內送 MDN 時傳回，進而產生不必要的 MDN 傳輸嘗試作業。</span><span class="sxs-lookup"><span data-stu-id="310be-105">Using a request-response receive port for an MDN would prevent a 200OK message from being returned in response to the incoming MDN, thereby causing unnecessary retries of the MDN transmission.</span></span>  
  
 <span data-ttu-id="310be-106">您可以使用 AS2Receive 或 AS2EdiReceive 管線來處理收到的 MDN。</span><span class="sxs-lookup"><span data-stu-id="310be-106">You can use either the AS2Receive or the AS2EdiReceive pipeline to process a received MDN.</span></span> <span data-ttu-id="310be-107">不過，如果您使用 AS2EdiReceive，您無法將 MDN 路由至 MessageBox 設定**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性**通知**頁面單向協議索引標籤。嘗試這樣做，將會造成 EDI 錯誤。因為 MSN 將會傳遞至 EDI 解碼器，但該解碼器並不能處理 MDN。</span><span class="sxs-lookup"><span data-stu-id="310be-107">However, if you use AS2EdiReceive, you cannot route the MDN into the MessageBox by setting the **Process inbound MDN into MessageBox for routing/delivery options** property on the **Acknowledgements** page of the one-way agreement tab. Trying to do so will result in an EDI error because the MSN will be passed to the EDI Decoder, which cannot process an MDN.</span></span> <span data-ttu-id="310be-108">如果 MDN 沒有傳送至 MessageBox，AS2Decoder 便會使用 MDN，這樣 MDN 便不會傳遞至 EDI 解碼器。</span><span class="sxs-lookup"><span data-stu-id="310be-108">If the MDN is not sent to the MessageBox, the AS2Decoder will consume the MDN, so it will not be passed to the EDI Decoder.</span></span>  
  
 <span data-ttu-id="310be-109">請使用下列組態來建立接收埠：</span><span class="sxs-lookup"><span data-stu-id="310be-109">Create the receive port with the following configuration:</span></span>  
  
|<span data-ttu-id="310be-110">位置</span><span class="sxs-lookup"><span data-stu-id="310be-110">Location</span></span>|<span data-ttu-id="310be-111">屬性</span><span class="sxs-lookup"><span data-stu-id="310be-111">Property</span></span>|<span data-ttu-id="310be-112">設定</span><span class="sxs-lookup"><span data-stu-id="310be-112">Setting</span></span>|  
|--------------|--------------|-------------|  
|<span data-ttu-id="310be-113">**接收埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="310be-113">**Receive Port Properties: General**</span></span>|<span data-ttu-id="310be-114">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="310be-114">Port type</span></span>|<span data-ttu-id="310be-115">單向</span><span class="sxs-lookup"><span data-stu-id="310be-115">One-Way</span></span>|  
|<span data-ttu-id="310be-116">**接收位置屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="310be-116">**Receive Location Properties: General**</span></span>|<span data-ttu-id="310be-117">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="310be-117">Transport Type</span></span>|<span data-ttu-id="310be-118">HTTP</span><span class="sxs-lookup"><span data-stu-id="310be-118">HTTP</span></span><br /><br /> <span data-ttu-id="310be-119">**請注意**只有 HTTP 配接器可以用於傳輸 Mdn，也就是 EDIINT/AS2 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="310be-119">**Note** Only the HTTP adapter can be used for transporting MDNs, which are EDIINT/AS2-encoded messages.</span></span> <span data-ttu-id="310be-120">這種傳輸無法搭配 HTTP 配接器以外的配接器運作。</span><span class="sxs-lookup"><span data-stu-id="310be-120">This transport will not work with an adapter other than the HTTP adapter.</span></span>|  
|<span data-ttu-id="310be-121">**接收位置屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="310be-121">**Receive Location Properties: General**</span></span>|<span data-ttu-id="310be-122">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="310be-122">Receive handler</span></span>|<span data-ttu-id="310be-123">BizTalkServerIsolatedHost</span><span class="sxs-lookup"><span data-stu-id="310be-123">BizTalkServerIsolatedHost</span></span>|  
|<span data-ttu-id="310be-124">**接收位置屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="310be-124">**Receive Location Properties: General**</span></span>|<span data-ttu-id="310be-125">接收管線</span><span class="sxs-lookup"><span data-stu-id="310be-125">Receive pipeline</span></span>|<span data-ttu-id="310be-126">AS2Receive 或 AS2EdiReceive</span><span class="sxs-lookup"><span data-stu-id="310be-126">AS2Receive or AS2EdiReceive</span></span>|  
|<span data-ttu-id="310be-127">**HTTP 傳輸屬性**</span><span class="sxs-lookup"><span data-stu-id="310be-127">**HTTP Transport Properties**</span></span>|<span data-ttu-id="310be-128">虛擬目錄加 ISAPI 延伸模組</span><span class="sxs-lookup"><span data-stu-id="310be-128">Virtual directory plus ISAPI extension</span></span>|<span data-ttu-id="310be-129">/\<虛擬目錄名稱\>/BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="310be-129">/\<name of virtual directory\>/BTSHTTPReceive.dll</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="310be-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="310be-130">See Also</span></span>  
 [<span data-ttu-id="310be-131">設定 AS2 解決方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="310be-131">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)