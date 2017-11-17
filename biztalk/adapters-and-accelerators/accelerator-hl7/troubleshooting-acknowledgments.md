---
title: "疑難排解通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, troubleshooting
- troubleshooting, acknowledgements
ms.assetid: faed356e-f5fc-4920-a9f9-82eca0ad7d67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbbb22498cfd3d451c0b8c75c8e6f4502c2364d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-acknowledgments"></a><span data-ttu-id="907b1-102">疑難排解通知</span><span class="sxs-lookup"><span data-stu-id="907b1-102">Troubleshooting Acknowledgments</span></span>
<span data-ttu-id="907b1-103">解決相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知。</span><span class="sxs-lookup"><span data-stu-id="907b1-103">Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] acknowledgments.</span></span>  
  
## <a name="acknowledgments-are-not-generated"></a><span data-ttu-id="907b1-104">不會產生通知</span><span class="sxs-lookup"><span data-stu-id="907b1-104">Acknowledgments are not generated</span></span>  
 <span data-ttu-id="907b1-105">有幾個可能的原因，通知 (Ack) 未產生或接收。</span><span class="sxs-lookup"><span data-stu-id="907b1-105">There are several potential causes for acknowledgments (ACKs) not being generated or received.</span></span> <span data-ttu-id="907b1-106">檢閱以下清單中的潛在問題。</span><span class="sxs-lookup"><span data-stu-id="907b1-106">Review the following list of potential problems.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-107">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-107">Symptom</span></span>  
 <span data-ttu-id="907b1-108">當您更新中的合作對象資訊時，不會產生通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管來產生通知。</span><span class="sxs-lookup"><span data-stu-id="907b1-108">Acknowledgments are not generated when you update party information in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to generate acknowledgments.</span></span>  
  
<span data-ttu-id="907b1-109">**可能的原因**:[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會快取和重新整理合作對象組態資訊每隔 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="907b1-109">**Possible cause** : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] caches and refreshes party configuration information every 15 minutes.</span></span>  
  
<span data-ttu-id="907b1-110">**解析**： 等待至少 15 分鐘的時間讓快取重新整理或重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]變更立即生效。</span><span class="sxs-lookup"><span data-stu-id="907b1-110">**Resolution** : Wait for at least 15 minutes for the cache to refresh, or restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for changes to take effect immediately.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-111">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-111">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="907b1-112">未產生通知，而且事件錯誤會出現在事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="907b1-112"> does not generate ACKs and event errors appear in the event log.</span></span>  
  
<span data-ttu-id="907b1-113">**可能的原因**： 無法產生通知，當批次中 / 出訊息的批次包含空白 FHS11 欄位。</span><span class="sxs-lookup"><span data-stu-id="907b1-113">**Possible cause** : An ACK cannot be generated when a batch in/batch out message contains an empty FHS11 field.</span></span>  
  
<span data-ttu-id="907b1-114">**解析**： 請確定您的郵件擁有正確格式化，並填入 FHS11 欄位。</span><span class="sxs-lookup"><span data-stu-id="907b1-114">**Resolution** : Ensure that your messages have a correctly formatted and populated FHS11 field.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-115">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-115">Symptom</span></span>  
 <span data-ttu-id="907b1-116">您的應用程式無法產生或收到通知。</span><span class="sxs-lookup"><span data-stu-id="907b1-116">Your application cannot generate or receive an ACK.</span></span>  
  
<span data-ttu-id="907b1-117">**可能的原因**: MSH3 欄位中的訊息不正確的資訊可避免[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]從傳送訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="907b1-117">**Possible cause** : Incorrect information in the MSH3 field of your message prevents [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] from sending the message ACKs.</span></span>  
  
<span data-ttu-id="907b1-118">**解析**： 請確定您的郵件擁有正確格式化，並填入 MSH3 欄位。</span><span class="sxs-lookup"><span data-stu-id="907b1-118">**Resolution** : Ensure that your messages have a correctly formatted and populated MSH3 field.</span></span>  
  
## <a name="acknowledgments-are-suspended-or-not-routed-to-the-send-party"></a><span data-ttu-id="907b1-119">通知會暫停，或者不會路由至傳送合作對象</span><span class="sxs-lookup"><span data-stu-id="907b1-119">Acknowledgments are suspended or not routed to the send party</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-120">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-120">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="907b1-121">將訊息傳送至雙向配接器中，而不會產生通知。</span><span class="sxs-lookup"><span data-stu-id="907b1-121"> sends messages to a two-way adapter without generating acknowledgments.</span></span>  
  
<span data-ttu-id="907b1-122">**可能的原因**： 訊息訂用帳戶未正確設定。</span><span class="sxs-lookup"><span data-stu-id="907b1-122">**Possible cause** : The message subscription is not configured correctly.</span></span>  
  
<span data-ttu-id="907b1-123">**解析**： 確定訊息訂閱已存在且設定正確。</span><span class="sxs-lookup"><span data-stu-id="907b1-123">**Resolution** : Ensure that message subscriptions are present and configured correctly.</span></span>  
  
## <a name="suspended-acknowledgments"></a><span data-ttu-id="907b1-124">暫止的通知</span><span class="sxs-lookup"><span data-stu-id="907b1-124">Suspended acknowledgments</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-125">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-125">Symptom</span></span>  
 <span data-ttu-id="907b1-126">通知會出現錯誤訊息"欄位中找到的 Delimiter"暫停時，您已設定合作對象具有編碼字元，例如其中包含分隔符號字元@-！ $。</span><span class="sxs-lookup"><span data-stu-id="907b1-126">Acknowledgments are suspended with the error message "Delimiter found in the field" when you have configured the party to have encoding characters containing delimiter characters such as @-!$.</span></span>  
  
<span data-ttu-id="907b1-127">**可能的原因**： 訊息包含例如句點 （.） 或連字號 （-） 字元。</span><span class="sxs-lookup"><span data-stu-id="907b1-127">**Possible cause** : The message contains characters such as a period (.) or a hyphen (-).</span></span> <span data-ttu-id="907b1-128">產生 Ack 時[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]包含"。"和"-"時間戳記值。</span><span class="sxs-lookup"><span data-stu-id="907b1-128">When generating the ACKs, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes "." and "-" for the timestamp value.</span></span>  
  
<span data-ttu-id="907b1-129">**解析**： 停用驗證，若要避免這些錯誤的傳送管線中。</span><span class="sxs-lookup"><span data-stu-id="907b1-129">**Resolution** : Disable validation in the send pipeline to avoid these errors.</span></span>  
  
## <a name="biztalk-server-generates-an-error-about-missing-ack-when-using-2-way-mllp-adapter"></a><span data-ttu-id="907b1-130">BizTalk Server 會產生有關遺漏 ACK，使用 2 方式 MLLP 配接器時錯誤</span><span class="sxs-lookup"><span data-stu-id="907b1-130">BizTalk Server generates an error about missing ACK when using 2-way MLLP adapter</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="907b1-131">徵兆</span><span class="sxs-lookup"><span data-stu-id="907b1-131">Symptom</span></span>  
 <span data-ttu-id="907b1-132">您可以取得下列或類似的錯誤事件記錄檔中：</span><span class="sxs-lookup"><span data-stu-id="907b1-132">You get the following or similar error in the Event Log:</span></span>  
  
 <span data-ttu-id="907b1-133">「 無法從網路，因為發生錯誤接收通知 」 來自 HRESULT 的例外狀況： 0xC0C01662""</span><span class="sxs-lookup"><span data-stu-id="907b1-133">"Unable to receive ACK from network due to error "Exception from HRESULT: 0xC0C01662""</span></span>  
  
<span data-ttu-id="907b1-134">**可能的原因**： 您正在使用 1 方式接收和 2 單向傳送埠，因此 BizTalk 沒有對應的接收埠，以傳回 2 單向傳送埠從接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="907b1-134">**Possible cause** : You are using 1-way receive and 2-way send port, so BizTalk does not have a corresponding Receive port to return the message received from the 2-way Send port.</span></span>  
  
<span data-ttu-id="907b1-135">**解析**： 這是根據設計，而且您可以忽略的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="907b1-135">**Resolution** : This is by design, and you can ignore the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907b1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="907b1-136">See Also</span></span>  
[<span data-ttu-id="907b1-137">HL7 中的疑難排解和已知問題</span><span class="sxs-lookup"><span data-stu-id="907b1-137">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)