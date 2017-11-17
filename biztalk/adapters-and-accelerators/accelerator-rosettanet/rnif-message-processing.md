---
title: "RNIF 訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RosettaNet Implementation Framework (RNIF)
- RosettaNet, about RosettaNet
- RNIF
- RNIF, non-repudiation
- RNIF, BizTalk Accelerator for RosettaNet
- non-repudiation
- RNIF, about RNIF
- BizTalk Accelerator for RosettaNet, RNIF
- RosettaNet
ms.assetid: 994f15bc-765c-4220-8ab1-176919e9e821
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34ff8794c6dcc94571607207b4c13e9dd2bf54cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rnif-message-processing"></a><span data-ttu-id="11498-102">RNIF 訊息處理</span><span class="sxs-lookup"><span data-stu-id="11498-102">RNIF Message Processing</span></span>
<span data-ttu-id="11498-103">RosettaNet 組織定義 RosettaNet 實作架構 (RNIF) 規格中的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="11498-103">The RosettaNet organization defines message exchange in the RosettaNet Implementation Framework (RNIF) specifications.</span></span> <span data-ttu-id="11498-104">RNIF 定義整合系統傳輸訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="11498-104">RNIF defines how integration systems will transport messages.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="11498-105">完整實作 RNIF 規格，將功能加入至功能[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]原生提供的方塊外。</span><span class="sxs-lookup"><span data-stu-id="11498-105"> fully implements the RNIF specifications, adding that functionality to what [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] natively provides out-of-the-box.</span></span>  
  
 <span data-ttu-id="11498-106">RNIF 通訊相當複雜。</span><span class="sxs-lookup"><span data-stu-id="11498-106">RNIF communications are complex.</span></span> <span data-ttu-id="11498-107">執行 RNIF 處理的公開程序包含各種不同的驗證檢查和複雜工作流程邏輯。</span><span class="sxs-lookup"><span data-stu-id="11498-107">The public processes that perform RNIF processing include a variety of validation checks and complex workflow logic.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="11498-108">原生提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="11498-108"> provides this functionality natively.</span></span> <span data-ttu-id="11498-109">這可讓您不需要從頭開發或維護 RNIF 邏輯，就能使用與 RosettaNet 相容的系統。</span><span class="sxs-lookup"><span data-stu-id="11498-109">This lets you use a RosettaNet-compliant system without developing or maintaining RNIF logic from scratch.</span></span>  
  
## <a name="btarn-support-for-rnif"></a><span data-ttu-id="11498-110">BTARN 對 RNIF 的支援</span><span class="sxs-lookup"><span data-stu-id="11498-110">BTARN Support for RNIF</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="11498-111">支援兩種 RNIF 版本： RNIF 1.1 與 RNIF 2.0 (V02.00.01)。</span><span class="sxs-lookup"><span data-stu-id="11498-111"> supports both versions of RNIF: RNIF 1.1 and RNIF 2.0 (V02.00.01).</span></span> <span data-ttu-id="11498-112">RNIF 2.0 已在 RNIF 1.1 支援的功能上新增重要功能，包括加密、附件和同步交易。</span><span class="sxs-lookup"><span data-stu-id="11498-112">RNIF 2.0 added significant functionality beyond that supported by RNIF 1.1, including encryption, attachments, and synchronous transactions.</span></span> <span data-ttu-id="11498-113">RNIF 2.0 對 RNIF 1.1 不具有回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="11498-113">RNIF 2.0 is not backward compatible with RNIF 1.1.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="11498-114"> 與 RosettaNet Ready RNIF 2.0 相容。</span><span class="sxs-lookup"><span data-stu-id="11498-114"> is RosettaNet Ready RNIF 2.0 compliant.</span></span>  
  
 <span data-ttu-id="11498-115">兩種版本以不同的方式定義 RosettaNet 訊息。</span><span class="sxs-lookup"><span data-stu-id="11498-115">The two versions define the RosettaNet message differently.</span></span> <span data-ttu-id="11498-116">如需有關不同訊息容器的詳細資訊，請參閱[RNIF 標準](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="11498-116">For more information about the different message containers, see [RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md).</span></span>  
  
 <span data-ttu-id="11498-117">整合系統透過 HTTP/HTTPS 及 SMTP; 執行 RNIF 傳送不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]實作只有 HTTP/HTTPS。</span><span class="sxs-lookup"><span data-stu-id="11498-117">Integration systems perform RNIF transfer over HTTP/HTTPS and SMTP; however, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements only HTTP/HTTPS.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="11498-118">在 RNIF 1.1 不支援附件和同步交易。</span><span class="sxs-lookup"><span data-stu-id="11498-118"> does not support attachments and synchronous transactions in RNIF 1.1.</span></span>  
  
### <a name="non-repudiation"></a><span data-ttu-id="11498-119">不可否認性</span><span class="sxs-lookup"><span data-stu-id="11498-119">Non-Repudiation</span></span>  
 <span data-ttu-id="11498-120">在 RNIF 標準中，不可否認性為必要條件。</span><span class="sxs-lookup"><span data-stu-id="11498-120">The RNIF standard includes a requirement for non-repudiation.</span></span> <span data-ttu-id="11498-121">基於此，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 所接收或傳送的任何傳輸格式訊息都會儲存到不可否認性資料庫，如此您可以證明已接收或傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="11498-121">This involves storing the wire format of any message received or sent by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] in a non-repudiation database, so that you can prove legally that you have received or sent it.</span></span> <span data-ttu-id="11498-122">由於此目的，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫中的 MessageStorageIn 資料表儲存內送訊息，並使用相同資料庫中的 MessageStorageOut 資料表儲存外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="11498-122">For this purpose, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the MessageStorageIn table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database for incoming messages and the MessageStorageOut table in the same database for outgoing messages.</span></span>  
  
 <span data-ttu-id="11498-123">在程序組態設定檔中個別設定服務內容及通知的不可否認性需求。</span><span class="sxs-lookup"><span data-stu-id="11498-123">You set non-repudiation requirements for service content and for acknowledgements separately in the process configuration profile.</span></span> <span data-ttu-id="11498-124">如果您設定一個或兩個**來源與內容的不可否認**和**不可否認性所需**選項，以`True`，然後[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會儲存下列資料：</span><span class="sxs-lookup"><span data-stu-id="11498-124">If you set one or both of the **Non-Repudiation of Origin and Content** and **Non-Repudiation Required** options to `True`, then [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will store the following data:</span></span>  
  
|<span data-ttu-id="11498-125">data</span><span class="sxs-lookup"><span data-stu-id="11498-125">Data</span></span>|<span data-ttu-id="11498-126">目錄</span><span class="sxs-lookup"><span data-stu-id="11498-126">Contents</span></span>|  
|----------|--------------|  
|<span data-ttu-id="11498-127">RecordID</span><span class="sxs-lookup"><span data-stu-id="11498-127">RecordID</span></span>|<span data-ttu-id="11498-128">所儲存訊息的專屬唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="11498-128">Proprietary unique ID of the stored message</span></span>|  
|<span data-ttu-id="11498-129">MessageCategory</span><span class="sxs-lookup"><span data-stu-id="11498-129">MessageCategory</span></span>|<span data-ttu-id="11498-130">要求 (0)、回應 (1) 或信號 (2)</span><span class="sxs-lookup"><span data-stu-id="11498-130">Request (0), Response (1), or Signal (2)</span></span>|  
|<span data-ttu-id="11498-131">DestinationParty</span><span class="sxs-lookup"><span data-stu-id="11498-131">DestinationParty</span></span>|<span data-ttu-id="11498-132">目的合作對象的名稱</span><span class="sxs-lookup"><span data-stu-id="11498-132">Name of the destination party</span></span>|  
|<span data-ttu-id="11498-133">SourceParty</span><span class="sxs-lookup"><span data-stu-id="11498-133">SourceParty</span></span>|<span data-ttu-id="11498-134">來源合作對象的名稱</span><span class="sxs-lookup"><span data-stu-id="11498-134">Name of the source party</span></span>|  
|<span data-ttu-id="11498-135">PIPCode</span><span class="sxs-lookup"><span data-stu-id="11498-135">PIPCode</span></span>|<span data-ttu-id="11498-136">例如，PIP3A4</span><span class="sxs-lookup"><span data-stu-id="11498-136">For example, PIP3A4</span></span>|  
|<span data-ttu-id="11498-137">PIPVersion</span><span class="sxs-lookup"><span data-stu-id="11498-137">PIPVersion</span></span>|<span data-ttu-id="11498-138">例如，V02.00</span><span class="sxs-lookup"><span data-stu-id="11498-138">For example, V02.00</span></span>|  
|<span data-ttu-id="11498-139">MessageContent</span><span class="sxs-lookup"><span data-stu-id="11498-139">MessageContent</span></span>|<span data-ttu-id="11498-140">二進位格式訊息</span><span class="sxs-lookup"><span data-stu-id="11498-140">Message in binary format</span></span>|  
|<span data-ttu-id="11498-141">MessageTrackingID</span><span class="sxs-lookup"><span data-stu-id="11498-141">MessageTrackingID</span></span>|<span data-ttu-id="11498-142">訊息的訊息追蹤識別碼</span><span class="sxs-lookup"><span data-stu-id="11498-142">Message tracking ID of the message</span></span>|  
|<span data-ttu-id="11498-143">PIPInstanceID</span><span class="sxs-lookup"><span data-stu-id="11498-143">PIPInstanceID</span></span>|<span data-ttu-id="11498-144">程序的 PIP 執行個體識別碼</span><span class="sxs-lookup"><span data-stu-id="11498-144">PIP instance ID of the process</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11498-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11498-145">See Also</span></span>  
 <span data-ttu-id="11498-146">[BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="11498-146">[What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="11498-147">PIP 實作</span><span class="sxs-lookup"><span data-stu-id="11498-147">PIP Implementation</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)