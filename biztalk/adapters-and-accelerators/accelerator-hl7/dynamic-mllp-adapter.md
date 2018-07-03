---
title: 動態 MLLP 配接器 |Microsoft Docs
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
ms.openlocfilehash: 0b1ad131716f5b1bb1b5abdfb7985fa93f2ae41c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999807"
---
# <a name="dynamic-mllp-adapter"></a><span data-ttu-id="a3807-102">動態 MLLP 配接器</span><span class="sxs-lookup"><span data-stu-id="a3807-102">Dynamic MLLP Adapter</span></span>
<span data-ttu-id="a3807-103">從開始[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]，MLLP 配接器屬性可以設定在執行階段使用單向或雙向 （要求-回應） 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a3807-103">Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], the MLLP adapter properties can be configured at Runtime using a One-Way or Two-Way (Request-Response) send port.</span></span>  
  
## <a name="dynamic-properties"></a><span data-ttu-id="a3807-104">動態屬性</span><span class="sxs-lookup"><span data-stu-id="a3807-104">Dynamic Properties</span></span>  
 <span data-ttu-id="a3807-105">下列屬性位於**GlobalPropertySchemas**命名空間：</span><span class="sxs-lookup"><span data-stu-id="a3807-105">The following properties are in the **GlobalPropertySchemas** namespace:</span></span>  
  
|<span data-ttu-id="a3807-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a3807-106">Property</span></span>|<span data-ttu-id="a3807-107">描述</span><span class="sxs-lookup"><span data-stu-id="a3807-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a3807-108">訊息 (MLLP.acceptableACKCodes) ="所有通知程式碼 」，</span><span class="sxs-lookup"><span data-stu-id="a3807-108">Message(MLLP.acceptableACKCodes)=”All ACK Codes”;</span></span>|<span data-ttu-id="a3807-109">數值包括：</span><span class="sxs-lookup"><span data-stu-id="a3807-109">Values include:</span></span><br /><br /> <span data-ttu-id="a3807-110">-所有通知代碼</span><span class="sxs-lookup"><span data-stu-id="a3807-110">-   All ACK Codes</span></span><br /><span data-ttu-id="a3807-111">-AA 和 CA</span><span class="sxs-lookup"><span data-stu-id="a3807-111">-   AA and CA</span></span><br /><span data-ttu-id="a3807-112">-AA、 CA、 AE 和 CE</span><span class="sxs-lookup"><span data-stu-id="a3807-112">-   AA, CA, AE and CE</span></span><br /><span data-ttu-id="a3807-113">-AA、 CA、 AR 及 CR</span><span class="sxs-lookup"><span data-stu-id="a3807-113">-   AA, CA, AR and CR</span></span><br /><br /> <span data-ttu-id="a3807-114">這是類似**接受通知碼**靜態 MLLP 傳送埠中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a3807-114">This is similar to the **Acceptable ACK Codes** property in a Static MLLP Send Port.</span></span>|  
|<span data-ttu-id="a3807-115">訊息 (MLLP。CarriageReturn) ="0 d";</span><span class="sxs-lookup"><span data-stu-id="a3807-115">Message(MLLP.CarriageReturn)=”0d”;</span></span>|<span data-ttu-id="a3807-116">ASCII 換行字元</span><span class="sxs-lookup"><span data-stu-id="a3807-116">ASCII Carriage Return Character</span></span>|  
|<span data-ttu-id="a3807-117">訊息 (MLLP.endBlockDelimiter) ="1 c";</span><span class="sxs-lookup"><span data-stu-id="a3807-117">Message(MLLP.endBlockDelimiter)=”1c”;</span></span>|<span data-ttu-id="a3807-118">結束區塊的 ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="a3807-118">ASCII End Block Character</span></span>|  
|<span data-ttu-id="a3807-119">訊息 (MLLP.startBlockDelimiter) ="0b";</span><span class="sxs-lookup"><span data-stu-id="a3807-119">Message(MLLP.startBlockDelimiter)=”0b”;</span></span>|<span data-ttu-id="a3807-120">開始區塊的 ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="a3807-120">ASCII Start Block Character</span></span>|  
|<span data-ttu-id="a3807-121">訊息 (MLLP.timeout) ="60000";</span><span class="sxs-lookup"><span data-stu-id="a3807-121">Message(MLLP.timeout)=”60000”;</span></span>|<span data-ttu-id="a3807-122">之後的非作用中的傳送通訊端上 BTAHL7 伺服器將會逾時期限 （0 為不會逾時）</span><span class="sxs-lookup"><span data-stu-id="a3807-122">Period after which inactive sending socket on BTAHL7 server will timeout(0 is no timeout)</span></span>|  
|<span data-ttu-id="a3807-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) ="127.0.0.1:11000";</span><span class="sxs-lookup"><span data-stu-id="a3807-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) = “127.0.0.1:11000”;</span></span>|<span data-ttu-id="a3807-124">位址和連接埠將訊息路由傳送</span><span class="sxs-lookup"><span data-stu-id="a3807-124">Address and Port for routing the message</span></span>|  
|<span data-ttu-id="a3807-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) ="MLLP";</span><span class="sxs-lookup"><span data-stu-id="a3807-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = “MLLP”;</span></span>|<span data-ttu-id="a3807-126">類型的配接器 (MLLP)</span><span class="sxs-lookup"><span data-stu-id="a3807-126">Type of Adapter (MLLP)</span></span>|  
  
## <a name="additional"></a><span data-ttu-id="a3807-127">其他</span><span class="sxs-lookup"><span data-stu-id="a3807-127">Additional</span></span>  
  
- <span data-ttu-id="a3807-128">HL7 協調流程中建立多部分訊息，請時，建立訊息組件在此順序：</span><span class="sxs-lookup"><span data-stu-id="a3807-128">When creating a multipart message in an orchestration for HL7, create the message parts in this following order:</span></span>  
  
  1. <span data-ttu-id="a3807-129">MSH 區段</span><span class="sxs-lookup"><span data-stu-id="a3807-129">MSH Segment</span></span>  
  
  2. <span data-ttu-id="a3807-130">BodySegments</span><span class="sxs-lookup"><span data-stu-id="a3807-130">BodySegments</span></span>  
  
  3. <span data-ttu-id="a3807-131">ZSegments</span><span class="sxs-lookup"><span data-stu-id="a3807-131">ZSegments</span></span>  
  
     <span data-ttu-id="a3807-132">如果您在不同的順序指定的訊息部分，就會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="a3807-132">If you specify the message parts in a different order, the following error occurs:</span></span>  
  
     <span data-ttu-id="a3807-133">WrongBodyPartException</span><span class="sxs-lookup"><span data-stu-id="a3807-133">WrongBodyPartException</span></span>  
  
- <span data-ttu-id="a3807-134">若要支援動態路由協調流程上，可以指定配接器路由屬性。</span><span class="sxs-lookup"><span data-stu-id="a3807-134">The adapter route properties can be specified on the orchestration to support dynamic routing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3807-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3807-135">See Also</span></span>  
 <span data-ttu-id="a3807-136">[組態參數，傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="a3807-136">[Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span></span>  
 <span data-ttu-id="a3807-137">[MLLP 接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="a3807-137">[MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span></span>  
 <span data-ttu-id="a3807-138">[MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="a3807-138">[MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span></span>  
 [<span data-ttu-id="a3807-139">處理 MLLP 編碼訊息</span><span class="sxs-lookup"><span data-stu-id="a3807-139">Processing MLLP-encoded Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)