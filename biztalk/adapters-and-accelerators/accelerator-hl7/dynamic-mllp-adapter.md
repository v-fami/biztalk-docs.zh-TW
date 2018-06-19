---
title: 動態 MLLP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e22fabb-0edf-4931-b8b2-74a5daccee4a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7d1d7046135de1dc1837d1fb8961ef440b5009
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204726"
---
# <a name="dynamic-mllp-adapter"></a><span data-ttu-id="25a07-102">動態 MLLP 配接器</span><span class="sxs-lookup"><span data-stu-id="25a07-102">Dynamic MLLP Adapter</span></span>
<span data-ttu-id="25a07-103">從開始[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]，MLLP 配接器屬性，可以在執行階段使用單向或雙向 （要求-回應） 傳送埠設定。</span><span class="sxs-lookup"><span data-stu-id="25a07-103">Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], the MLLP adapter properties can be configured at Runtime using a One-Way or Two-Way (Request-Response) send port.</span></span>  
  
## <a name="dynamic-properties"></a><span data-ttu-id="25a07-104">動態屬性</span><span class="sxs-lookup"><span data-stu-id="25a07-104">Dynamic Properties</span></span>  
 <span data-ttu-id="25a07-105">下列屬性處於**GlobalPropertySchemas**命名空間：</span><span class="sxs-lookup"><span data-stu-id="25a07-105">The following properties are in the **GlobalPropertySchemas** namespace:</span></span>  
  
|<span data-ttu-id="25a07-106">屬性</span><span class="sxs-lookup"><span data-stu-id="25a07-106">Property</span></span>|<span data-ttu-id="25a07-107">Description</span><span class="sxs-lookup"><span data-stu-id="25a07-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="25a07-108">訊息 (MLLP.acceptableACKCodes) = 「 所有通知代碼 」。</span><span class="sxs-lookup"><span data-stu-id="25a07-108">Message(MLLP.acceptableACKCodes)=”All ACK Codes”;</span></span>|<span data-ttu-id="25a07-109">數值包括：</span><span class="sxs-lookup"><span data-stu-id="25a07-109">Values include:</span></span><br /><br /> <span data-ttu-id="25a07-110">-所有通知代碼</span><span class="sxs-lookup"><span data-stu-id="25a07-110">-   All ACK Codes</span></span><br /><span data-ttu-id="25a07-111">-AA 和 CA</span><span class="sxs-lookup"><span data-stu-id="25a07-111">-   AA and CA</span></span><br /><span data-ttu-id="25a07-112">-AA、 CA、 AE 和 CE</span><span class="sxs-lookup"><span data-stu-id="25a07-112">-   AA, CA, AE and CE</span></span><br /><span data-ttu-id="25a07-113">-AA、 CA、 AR 和 CR</span><span class="sxs-lookup"><span data-stu-id="25a07-113">-   AA, CA, AR and CR</span></span><br /><br /> <span data-ttu-id="25a07-114">這是類似於**接受通知碼**靜態 MLLP 傳送埠中的屬性。</span><span class="sxs-lookup"><span data-stu-id="25a07-114">This is similar to the **Acceptable ACK Codes** property in a Static MLLP Send Port.</span></span>|  
|<span data-ttu-id="25a07-115">訊息 (MLLP。CarriageReturn) ="0 d"。</span><span class="sxs-lookup"><span data-stu-id="25a07-115">Message(MLLP.CarriageReturn)=”0d”;</span></span>|<span data-ttu-id="25a07-116">ASCII 歸位字元</span><span class="sxs-lookup"><span data-stu-id="25a07-116">ASCII Carriage Return Character</span></span>|  
|<span data-ttu-id="25a07-117">訊息 (MLLP.endBlockDelimiter) ="1 c";</span><span class="sxs-lookup"><span data-stu-id="25a07-117">Message(MLLP.endBlockDelimiter)=”1c”;</span></span>|<span data-ttu-id="25a07-118">ASCII 結束區塊字元</span><span class="sxs-lookup"><span data-stu-id="25a07-118">ASCII End Block Character</span></span>|  
|<span data-ttu-id="25a07-119">訊息 (MLLP.startBlockDelimiter) ="0b";</span><span class="sxs-lookup"><span data-stu-id="25a07-119">Message(MLLP.startBlockDelimiter)=”0b”;</span></span>|<span data-ttu-id="25a07-120">開始區塊的 ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="25a07-120">ASCII Start Block Character</span></span>|  
|<span data-ttu-id="25a07-121">訊息 (MLLP.timeout) ="60000";</span><span class="sxs-lookup"><span data-stu-id="25a07-121">Message(MLLP.timeout)=”60000”;</span></span>|<span data-ttu-id="25a07-122">後的非作用中的傳送通訊端上 BTAHL7 伺服器將會逾時期間內 （0 為不會逾時）</span><span class="sxs-lookup"><span data-stu-id="25a07-122">Period after which inactive sending socket on BTAHL7 server will timeout(0 is no timeout)</span></span>|  
|<span data-ttu-id="25a07-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) ="127.0.0.1:11000";</span><span class="sxs-lookup"><span data-stu-id="25a07-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) = “127.0.0.1:11000”;</span></span>|<span data-ttu-id="25a07-124">位址和連接埠將訊息路由傳送</span><span class="sxs-lookup"><span data-stu-id="25a07-124">Address and Port for routing the message</span></span>|  
|<span data-ttu-id="25a07-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) ="MLLP";</span><span class="sxs-lookup"><span data-stu-id="25a07-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = “MLLP”;</span></span>|<span data-ttu-id="25a07-126">類型的配接器 (MLLP)</span><span class="sxs-lookup"><span data-stu-id="25a07-126">Type of Adapter (MLLP)</span></span>|  
  
## <a name="additional"></a><span data-ttu-id="25a07-127">其他</span><span class="sxs-lookup"><span data-stu-id="25a07-127">Additional</span></span>  
  
-   <span data-ttu-id="25a07-128">當 HL7 協調流程中建立多部分訊息，訊息部分在建立此順序：</span><span class="sxs-lookup"><span data-stu-id="25a07-128">When creating a multipart message in an orchestration for HL7, create the message parts in this following order:</span></span>  
  
    1.  <span data-ttu-id="25a07-129">MSH 區段</span><span class="sxs-lookup"><span data-stu-id="25a07-129">MSH Segment</span></span>  
  
    2.  <span data-ttu-id="25a07-130">BodySegments</span><span class="sxs-lookup"><span data-stu-id="25a07-130">BodySegments</span></span>  
  
    3.  <span data-ttu-id="25a07-131">ZSegments</span><span class="sxs-lookup"><span data-stu-id="25a07-131">ZSegments</span></span>  
  
     <span data-ttu-id="25a07-132">如果您以不同順序指定的訊息部分，就會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="25a07-132">If you specify the message parts in a different order, the following error occurs:</span></span>  
  
     <span data-ttu-id="25a07-133">WrongBodyPartException</span><span class="sxs-lookup"><span data-stu-id="25a07-133">WrongBodyPartException</span></span>  
  
-   <span data-ttu-id="25a07-134">若要支援動態路由協調流程上，可以指定配接器路由屬性。</span><span class="sxs-lookup"><span data-stu-id="25a07-134">The adapter route properties can be specified on the orchestration to support dynamic routing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a07-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25a07-135">See Also</span></span>  
 <span data-ttu-id="25a07-136">[組態參數傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="25a07-136">[Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span></span>  
 <span data-ttu-id="25a07-137">[MLLP 的接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="25a07-137">[MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span></span>  
 <span data-ttu-id="25a07-138">[MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="25a07-138">[MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span></span>  
 [<span data-ttu-id="25a07-139">處理 MLLP 編碼訊息</span><span class="sxs-lookup"><span data-stu-id="25a07-139">Processing MLLP-encoded Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)