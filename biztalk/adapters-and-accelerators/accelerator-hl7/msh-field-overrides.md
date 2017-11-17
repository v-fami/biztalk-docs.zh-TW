---
title: "MSH 欄位覆寫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- headers, overriding
- MSH Map tab [Configuration Explorer]
- headers, MSH Map tab
- messages, message headers
ms.assetid: f5b2c820-57e7-4a56-9d9f-713563bd7335
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82603ded113fa25c839661fb7874d97f8b3bb074
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="msh-field-overrides"></a><span data-ttu-id="69cee-102">MSH 欄位覆寫</span><span class="sxs-lookup"><span data-stu-id="69cee-102">MSH Field Overrides</span></span>
<span data-ttu-id="69cee-103">每個 HL7 訊息具有訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-103">Every HL7 message has a message header.</span></span> <span data-ttu-id="69cee-104">使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以覆寫您的商務需求為基礎的任何訊息標頭值。</span><span class="sxs-lookup"><span data-stu-id="69cee-104">Using [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], you can override any message header value based on your business need.</span></span> <span data-ttu-id="69cee-105">您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤，以手動方式覆寫訊息標頭值而不使用任何對應或協調流程。</span><span class="sxs-lookup"><span data-stu-id="69cee-105">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH Map** tab to manually over ride message header values without using any mapping or orchestration.</span></span>  
  
## <a name="configuring-msh-field-overrides"></a><span data-ttu-id="69cee-106">MSH 欄位的設定會覆寫</span><span class="sxs-lookup"><span data-stu-id="69cee-106">Configuring MSH Field Overrides</span></span>  
 <span data-ttu-id="69cee-107">您使用**MSH 對應**索引標籤中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 (在高階**合作對象** 索引標籤) 設定 MSH 欄位覆寫。</span><span class="sxs-lookup"><span data-stu-id="69cee-107">You use the **MSH Map** tab in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (under the high-level **Parties** tab) to configure MSH field overrides.</span></span> <span data-ttu-id="69cee-108">MSH 中現有的值輸出 HL7 訊息時使用的值覆寫這個索引標籤的 MSH 欄位中輸入值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將傳送至選取的合作對象。</span><span class="sxs-lookup"><span data-stu-id="69cee-108">When you enter a value for an MSH field using this tab, that value overrides the existing MSH value in an outbound HL7 message that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends to the selected party.</span></span> <span data-ttu-id="69cee-109">您可以輸入新的值，有許多的 MSH 欄位，或從 MSH15 和 MSH16 欄位的下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="69cee-109">You can type new values for many MSH fields, or select values from a drop-down list for the MSH15 and MSH16 fields.</span></span>  
  
 <span data-ttu-id="69cee-110">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="69cee-110">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH Map** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-msh.gif "hl7_ops_msh")  
  
 <span data-ttu-id="69cee-111">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管並設定 MSH 欄位覆寫。</span><span class="sxs-lookup"><span data-stu-id="69cee-111">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure MSH field overrides.</span></span>  
  
#### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="69cee-112">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="69cee-112">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="69cee-113">按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本 > Accelerator for HL7**，然後按一下  **BTAHL7組態總管**。</span><span class="sxs-lookup"><span data-stu-id="69cee-113">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
#### <a name="to-configure-msh-field-overrides"></a><span data-ttu-id="69cee-114">若要設定的覆寫 MSH 欄位</span><span class="sxs-lookup"><span data-stu-id="69cee-114">To configure MSH field overrides</span></span>  
  
1.  <span data-ttu-id="69cee-115">BTAHL7 組態總管 中，在上**MSH 對應**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="69cee-115">In BTAHL7 Configuration Explorer, on the **MSH Map** tab, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69cee-116">若要覆寫現有的值為 null，請輸入 **\\** 。</span><span class="sxs-lookup"><span data-stu-id="69cee-116">To override the existing value to null, type **\\**.</span></span>  
  
    |<span data-ttu-id="69cee-117">使用</span><span class="sxs-lookup"><span data-stu-id="69cee-117">Use this</span></span>|<span data-ttu-id="69cee-118">動作</span><span class="sxs-lookup"><span data-stu-id="69cee-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="69cee-119">**MSH.3**</span><span class="sxs-lookup"><span data-stu-id="69cee-119">**MSH.3**</span></span>|<span data-ttu-id="69cee-120">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-120">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-121">**MSH.4**</span><span class="sxs-lookup"><span data-stu-id="69cee-121">**MSH.4**</span></span>|<span data-ttu-id="69cee-122">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-122">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-123">**MSH.5**</span><span class="sxs-lookup"><span data-stu-id="69cee-123">**MSH.5**</span></span>|<span data-ttu-id="69cee-124">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-124">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-125">**MSH.6**</span><span class="sxs-lookup"><span data-stu-id="69cee-125">**MSH.6**</span></span>|<span data-ttu-id="69cee-126">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-126">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-127">**MSH.8**</span><span class="sxs-lookup"><span data-stu-id="69cee-127">**MSH.8**</span></span>|<span data-ttu-id="69cee-128">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-128">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-129">**MSH.9**</span><span class="sxs-lookup"><span data-stu-id="69cee-129">**MSH.9**</span></span>|<span data-ttu-id="69cee-130">訊息類型 欄位會覆寫此訊息標頭</span><span class="sxs-lookup"><span data-stu-id="69cee-130">Type message field overrides for this message header</span></span>|  
    |<span data-ttu-id="69cee-131">**MSH.12**</span><span class="sxs-lookup"><span data-stu-id="69cee-131">**MSH.12**</span></span>|<span data-ttu-id="69cee-132">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="69cee-132">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="69cee-133">**MSH.15**</span><span class="sxs-lookup"><span data-stu-id="69cee-133">**MSH.15**</span></span>|<span data-ttu-id="69cee-134">選取從接受通知類型的通知覆寫下列選項：</span><span class="sxs-lookup"><span data-stu-id="69cee-134">Select from the following options for an acknowledgment override for the accept acknowledgment type:</span></span><br /><br /> <span data-ttu-id="69cee-135">-   **AL**。</span><span class="sxs-lookup"><span data-stu-id="69cee-135">-   **AL**.</span></span> <span data-ttu-id="69cee-136">選取此選項，如果您一定想要傳送接受通知。</span><span class="sxs-lookup"><span data-stu-id="69cee-136">Select this option if you always want to send accept acknowledgments.</span></span><br /><span data-ttu-id="69cee-137">-   **NE**。</span><span class="sxs-lookup"><span data-stu-id="69cee-137">-   **NE**.</span></span> <span data-ttu-id="69cee-138">選取此選項，如果您不想要傳送接受通知。</span><span class="sxs-lookup"><span data-stu-id="69cee-138">Select this option if you never want to send accept acknowledgments.</span></span><br /><span data-ttu-id="69cee-139">-   **SU**。</span><span class="sxs-lookup"><span data-stu-id="69cee-139">-   **SU**.</span></span> <span data-ttu-id="69cee-140">選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。</span><span class="sxs-lookup"><span data-stu-id="69cee-140">Select this option if you want to send accept acknowledgments after successful transmission of a message.</span></span><br /><span data-ttu-id="69cee-141">-   **ER**。</span><span class="sxs-lookup"><span data-stu-id="69cee-141">-   **ER**.</span></span> <span data-ttu-id="69cee-142">如果您想要傳送，請選取此選項只會發生錯誤時接受通知。</span><span class="sxs-lookup"><span data-stu-id="69cee-142">Select this option if you want to send accept acknowledgments only in the event of an error.</span></span>|  
    |<span data-ttu-id="69cee-143">**MSH.16**</span><span class="sxs-lookup"><span data-stu-id="69cee-143">**MSH.16**</span></span>|<span data-ttu-id="69cee-144">選取此選項，從應用程式通知類型的通知覆寫下列選項：</span><span class="sxs-lookup"><span data-stu-id="69cee-144">Select from the following options for an acknowledgment override for the application acknowledgment type:</span></span><br /><br /> <span data-ttu-id="69cee-145">-   **AL**。</span><span class="sxs-lookup"><span data-stu-id="69cee-145">-   **AL**.</span></span> <span data-ttu-id="69cee-146">如果您一定想要傳送的應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69cee-146">Select this option if you always want to send application acknowledgments.</span></span><br /><span data-ttu-id="69cee-147">-   **NE**。</span><span class="sxs-lookup"><span data-stu-id="69cee-147">-   **NE**.</span></span> <span data-ttu-id="69cee-148">如果您不想要傳送應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69cee-148">Select this option if you never want to send application acknowledgments.</span></span><br /><span data-ttu-id="69cee-149">-   **SU**。</span><span class="sxs-lookup"><span data-stu-id="69cee-149">-   **SU**.</span></span> <span data-ttu-id="69cee-150">如果您想要將訊息傳輸成功之後傳送應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69cee-150">Select this option if you want to send application acknowledgments after successful transmission of a message.</span></span><br /><span data-ttu-id="69cee-151">-   **ER**。</span><span class="sxs-lookup"><span data-stu-id="69cee-151">-   **ER**.</span></span> <span data-ttu-id="69cee-152">如果您想要傳送的應用程式通知只會發生錯誤時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="69cee-152">Select this option if you want to send application acknowledgments only in the event of an error.</span></span>|  
  
2.  <span data-ttu-id="69cee-153">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="69cee-153">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69cee-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69cee-154">See Also</span></span>  
 <span data-ttu-id="69cee-155">[記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="69cee-155">[Logging Configuration](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span></span>  
 <span data-ttu-id="69cee-156">[訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="69cee-156">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
[<span data-ttu-id="69cee-157">作業記錄、 訊息批次、 驗證和 asknowledgment 設定</span><span class="sxs-lookup"><span data-stu-id="69cee-157">Operational logging, message batching, validation and asknowledgment settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)