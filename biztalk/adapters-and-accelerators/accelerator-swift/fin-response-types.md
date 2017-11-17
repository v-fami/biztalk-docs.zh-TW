---
title: "FIN 回應類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, response types
- deploying, schemas
- FIN Response Reconciliation, message types
- FRR, deploying schemas
- schemas, deploying
- FIN Response Reconciliation, response types
- messages, message types
- response types [FIN Response Reconciliation]
ms.assetid: a6ef2f20-08ab-40d3-a0a5-cc4048ce0987
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54c890a5e0f51207cce1897b10095a87ae438793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-types"></a><span data-ttu-id="fd564-102">FIN 回應類型</span><span class="sxs-lookup"><span data-stu-id="fd564-102">FIN Response Types</span></span>
<span data-ttu-id="fd564-103">FIN 回應對帳 (FRR) 會調解任何類別 0 到 9 的 SWIFT FIN 訊息的回應。</span><span class="sxs-lookup"><span data-stu-id="fd564-103">FIN Response Reconciliation (FRR) reconciles responses to any Category 0 to 9 SWIFT FIN message.</span></span> <span data-ttu-id="fd564-104">在其中一個 FIN 訊息回應，SWIFT FIN 應用程式一定會傳送至少一個，可能是多個一個通知 (ACK) 或負值通知 (NAK)。</span><span class="sxs-lookup"><span data-stu-id="fd564-104">In response to one of these FIN messages, the SWIFT FIN application always sends at least one, and possibly more than one, acknowledgment (ACK) or negative acknowledgment (NAK).</span></span> <span data-ttu-id="fd564-105">下表顯示訊息類型的傳出和傳入 （回應） FRR 處理訊息。</span><span class="sxs-lookup"><span data-stu-id="fd564-105">The following table shows the message types of the outbound and inbound (response) messages processed by FRR.</span></span>  
  
|<span data-ttu-id="fd564-106">輸出 /</span><span class="sxs-lookup"><span data-stu-id="fd564-106">Outbound/</span></span><br /><br /> <span data-ttu-id="fd564-107">輸入</span><span class="sxs-lookup"><span data-stu-id="fd564-107">inbound</span></span>|<span data-ttu-id="fd564-108">訊息類型</span><span class="sxs-lookup"><span data-stu-id="fd564-108">Message type</span></span>|<span data-ttu-id="fd564-109">訊息狀態</span><span class="sxs-lookup"><span data-stu-id="fd564-109">Message status</span></span>|  
|----------------------------|------------------|--------------------|  
|<span data-ttu-id="fd564-110">輸出</span><span class="sxs-lookup"><span data-stu-id="fd564-110">Outbound</span></span>|<span data-ttu-id="fd564-111">所有類別 0 到 9 SWIFT FIN 訊息類型</span><span class="sxs-lookup"><span data-stu-id="fd564-111">All Category 0 to 9 SWIFT FIN message types</span></span>|<span data-ttu-id="fd564-112">不適用</span><span class="sxs-lookup"><span data-stu-id="fd564-112">N/A</span></span>|  
|<span data-ttu-id="fd564-113">輸入</span><span class="sxs-lookup"><span data-stu-id="fd564-113">Inbound</span></span>|<span data-ttu-id="fd564-114">MQ 系列取景位置調整/NAN (MQ Series 傳輸層級 ACK/NAK)</span><span class="sxs-lookup"><span data-stu-id="fd564-114">MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)</span></span>|<span data-ttu-id="fd564-115">MQSeries 傳輸通知</span><span class="sxs-lookup"><span data-stu-id="fd564-115">MQSeries transport acknowledgment</span></span>|  
||<span data-ttu-id="fd564-116">MT010 （非傳遞警告）</span><span class="sxs-lookup"><span data-stu-id="fd564-116">MT010 (Non-Delivery Warning)</span></span>|<span data-ttu-id="fd564-117">SWIFT 成功傳送原始訊息給夥伴，但夥伴已收到訊息的指示。</span><span class="sxs-lookup"><span data-stu-id="fd564-117">SWIFT successfully sent the original message to the partner, but has no indication that the partner received the message.</span></span> <span data-ttu-id="fd564-118">如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]收到多個未傳遞警告 (NDW) 訊息，執行迴圈，並等候下一個預期的訊息。</span><span class="sxs-lookup"><span data-stu-id="fd564-118">If [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives multiple Non-Delivery Warning (NDW) messages, it loops and waits for the next expected message.</span></span>|  
||<span data-ttu-id="fd564-119">MT011 （傳遞通知）</span><span class="sxs-lookup"><span data-stu-id="fd564-119">MT011 (Delivery Notification)</span></span>|<span data-ttu-id="fd564-120">SWIFT 成功傳送原始訊息給夥伴，並接收夥伴已收到訊息的指示。</span><span class="sxs-lookup"><span data-stu-id="fd564-120">SWIFT successfully sent the original message to the partner, and received an indication that the partner received the message.</span></span>|  
||<span data-ttu-id="fd564-121">MT012 （寄件者通知）</span><span class="sxs-lookup"><span data-stu-id="fd564-121">MT012 (Sender Notification)</span></span>|<span data-ttu-id="fd564-122">SWIFT 已順利接收原始訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd564-122">SWIFT successfully received the original message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>|  
||<span data-ttu-id="fd564-123">MT015 （DNK 或延遲的 NAK）</span><span class="sxs-lookup"><span data-stu-id="fd564-123">MT015 (DNK, or Delayed NAK)</span></span>|<span data-ttu-id="fd564-124">SWIFT 尚未成功傳送原始訊息給夥伴。</span><span class="sxs-lookup"><span data-stu-id="fd564-124">SWIFT has not successfully sent the original message to the partner.</span></span>|  
||<span data-ttu-id="fd564-125">MT019 （中止通知）</span><span class="sxs-lookup"><span data-stu-id="fd564-125">MT019 (Abort Notification)</span></span>|<span data-ttu-id="fd564-126">在 SWIFT 中止訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="fd564-126">Message transmission aborted at SWIFT.</span></span>|  
||<span data-ttu-id="fd564-127">MTS21_FIN_ACKNAK （認可或負值通知 (ACK/NAK) LT 傳送 FIN 訊息）</span><span class="sxs-lookup"><span data-stu-id="fd564-127">MTS21_FIN_ACKNAK (Acknowledgment or negative acknowledgment of a FIN message sent by an LT (ACK/NAK))</span></span>|<span data-ttu-id="fd564-128">SWIFT 成功或失敗訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd564-128">SWIFT successfully or unsuccessfully received the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="fd564-129">此訊息會涵蓋這兩種案例。</span><span class="sxs-lookup"><span data-stu-id="fd564-129">This message covers both of these cases.</span></span> <span data-ttu-id="fd564-130">它是通知或 NAK 取決於訊息 ("0"代表 ACK) 和"1"的 NAK 451 欄位中的值。</span><span class="sxs-lookup"><span data-stu-id="fd564-130">Whether it is an ACK or a NAK is determined by the value in the 451 field of the message ("0" for ACK and "1" for NAK).</span></span> <span data-ttu-id="fd564-131">這會是第一個回應傳送回[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd564-131">This will be the first response delivered back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>|  
  
## <a name="deployment-of-schemas-for-frr"></a><span data-ttu-id="fd564-132">部署結構描述的 FRR</span><span class="sxs-lookup"><span data-stu-id="fd564-132">Deployment of Schemas for FRR</span></span>  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="fd564-133">安裝程式 （如上述表格中所示），將部署 FrrSchemas.dll 中的所有系統層級訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="fd564-133"> setup deploys schemas in FrrSchemas.dll for all system-level messages (as shown in the table above).</span></span> <span data-ttu-id="fd564-134">FRR 協調流程需要部署這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="fd564-134">The FRR orchestration requires these schemas to be deployed.</span></span> <span data-ttu-id="fd564-135">因為[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會部署在 FrrSchemas.dll 這些結構描述，您不必，並不是，必須部署這些結構描述，另一個專案中的。</span><span class="sxs-lookup"><span data-stu-id="fd564-135">Because [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup deploys these schemas in FrrSchemas.dll, you do not have to, and must not, deploy these schemas in another project.</span></span> <span data-ttu-id="fd564-136">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd564-136">Doing so will generate an error.</span></span>  
  
 <span data-ttu-id="fd564-137">FRRSchemas.dll 包含下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="fd564-137">FRRSchemas.dll includes the following schemas:</span></span>  
  
-   <span data-ttu-id="fd564-138">TransportAck</span><span class="sxs-lookup"><span data-stu-id="fd564-138">TransportAck</span></span>  
  
-   <span data-ttu-id="fd564-139">MT010</span><span class="sxs-lookup"><span data-stu-id="fd564-139">MT010</span></span>  
  
-   <span data-ttu-id="fd564-140">MT011</span><span class="sxs-lookup"><span data-stu-id="fd564-140">MT011</span></span>  
  
-   <span data-ttu-id="fd564-141">MT012</span><span class="sxs-lookup"><span data-stu-id="fd564-141">MT012</span></span>  
  
-   <span data-ttu-id="fd564-142">MT015</span><span class="sxs-lookup"><span data-stu-id="fd564-142">MT015</span></span>  
  
-   <span data-ttu-id="fd564-143">MT019</span><span class="sxs-lookup"><span data-stu-id="fd564-143">MT019</span></span>  
  
-   <span data-ttu-id="fd564-144">MTS21_FIN_ACKNAK</span><span class="sxs-lookup"><span data-stu-id="fd564-144">MTS21_FIN_ACKNAK</span></span>