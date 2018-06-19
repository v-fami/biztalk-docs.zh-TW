---
title: MSH 欄位覆寫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- headers, overriding
- MSH Map tab [Configuration Explorer]
- headers, MSH Map tab
- messages, message headers
ms.assetid: f5b2c820-57e7-4a56-9d9f-713563bd7335
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7303de4a8054cfe9f7140bd6eb548c228248777c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961020"
---
# <a name="msh-field-overrides"></a><span data-ttu-id="80903-102">MSH 欄位覆寫</span><span class="sxs-lookup"><span data-stu-id="80903-102">MSH Field Overrides</span></span>
<span data-ttu-id="80903-103">每個 HL7 訊息具有訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-103">Every HL7 message has a message header.</span></span> <span data-ttu-id="80903-104">使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以覆寫您的商務需求為基礎的任何訊息標頭值。</span><span class="sxs-lookup"><span data-stu-id="80903-104">Using [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], you can override any message header value based on your business need.</span></span> <span data-ttu-id="80903-105">您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤，以手動方式覆寫訊息標頭值而不使用任何對應或協調流程。</span><span class="sxs-lookup"><span data-stu-id="80903-105">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH Map** tab to manually over ride message header values without using any mapping or orchestration.</span></span>  
  
## <a name="configuring-msh-field-overrides"></a><span data-ttu-id="80903-106">MSH 欄位的設定會覆寫</span><span class="sxs-lookup"><span data-stu-id="80903-106">Configuring MSH Field Overrides</span></span>  
 <span data-ttu-id="80903-107">您使用**MSH 對應**索引標籤中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 (在高階**合作對象** 索引標籤) 設定 MSH 欄位覆寫。</span><span class="sxs-lookup"><span data-stu-id="80903-107">You use the **MSH Map** tab in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (under the high-level **Parties** tab) to configure MSH field overrides.</span></span> <span data-ttu-id="80903-108">MSH 中現有的值輸出 HL7 訊息時使用的值覆寫這個索引標籤的 MSH 欄位中輸入值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將傳送至選取的合作對象。</span><span class="sxs-lookup"><span data-stu-id="80903-108">When you enter a value for an MSH field using this tab, that value overrides the existing MSH value in an outbound HL7 message that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends to the selected party.</span></span> <span data-ttu-id="80903-109">您可以輸入新的值，有許多的 MSH 欄位，或從 MSH15 和 MSH16 欄位的下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="80903-109">You can type new values for many MSH fields, or select values from a drop-down list for the MSH15 and MSH16 fields.</span></span>  
  
 <span data-ttu-id="80903-110">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80903-110">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH Map** tab.</span></span>  
  
 <span data-ttu-id="80903-111">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-msh.gif "hl7_ops_msh")</span><span class="sxs-lookup"><span data-stu-id="80903-111">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-msh.gif "hl7_ops_msh")</span></span>  
  
 <span data-ttu-id="80903-112">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管並設定 MSH 欄位覆寫。</span><span class="sxs-lookup"><span data-stu-id="80903-112">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure MSH field overrides.</span></span>  
  
#### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="80903-113">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="80903-113">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="80903-114">按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="80903-114">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
#### <a name="to-configure-msh-field-overrides"></a><span data-ttu-id="80903-115">若要設定的覆寫 MSH 欄位</span><span class="sxs-lookup"><span data-stu-id="80903-115">To configure MSH field overrides</span></span>  
  
1.  <span data-ttu-id="80903-116">BTAHL7 組態總管 中，在上**MSH 對應**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="80903-116">In BTAHL7 Configuration Explorer, on the **MSH Map** tab, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="80903-117">若要覆寫現有的值為 null，請輸入 **\\** 。</span><span class="sxs-lookup"><span data-stu-id="80903-117">To override the existing value to null, type **\\**.</span></span>  
  
    |<span data-ttu-id="80903-118">使用</span><span class="sxs-lookup"><span data-stu-id="80903-118">Use this</span></span>|<span data-ttu-id="80903-119">動作</span><span class="sxs-lookup"><span data-stu-id="80903-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="80903-120">**MSH.3**</span><span class="sxs-lookup"><span data-stu-id="80903-120">**MSH.3**</span></span>|<span data-ttu-id="80903-121">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-121">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-122">**MSH.4**</span><span class="sxs-lookup"><span data-stu-id="80903-122">**MSH.4**</span></span>|<span data-ttu-id="80903-123">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-123">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-124">**MSH.5**</span><span class="sxs-lookup"><span data-stu-id="80903-124">**MSH.5**</span></span>|<span data-ttu-id="80903-125">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-125">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-126">**MSH.6**</span><span class="sxs-lookup"><span data-stu-id="80903-126">**MSH.6**</span></span>|<span data-ttu-id="80903-127">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-127">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-128">**MSH.8**</span><span class="sxs-lookup"><span data-stu-id="80903-128">**MSH.8**</span></span>|<span data-ttu-id="80903-129">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-129">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-130">**MSH.9**</span><span class="sxs-lookup"><span data-stu-id="80903-130">**MSH.9**</span></span>|<span data-ttu-id="80903-131">訊息類型 欄位會覆寫此訊息標頭</span><span class="sxs-lookup"><span data-stu-id="80903-131">Type message field overrides for this message header</span></span>|  
    |<span data-ttu-id="80903-132">**MSH.12**</span><span class="sxs-lookup"><span data-stu-id="80903-132">**MSH.12**</span></span>|<span data-ttu-id="80903-133">訊息類型 欄位會覆寫此訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="80903-133">Type message field overrides for this message header.</span></span>|  
    |<span data-ttu-id="80903-134">**MSH.15**</span><span class="sxs-lookup"><span data-stu-id="80903-134">**MSH.15**</span></span>|<span data-ttu-id="80903-135">選取從接受通知類型的通知覆寫下列選項：</span><span class="sxs-lookup"><span data-stu-id="80903-135">Select from the following options for an acknowledgment override for the accept acknowledgment type:</span></span><br /><br /> <span data-ttu-id="80903-136">-   **AL**。</span><span class="sxs-lookup"><span data-stu-id="80903-136">-   **AL**.</span></span> <span data-ttu-id="80903-137">選取此選項，如果您一定想要傳送接受通知。</span><span class="sxs-lookup"><span data-stu-id="80903-137">Select this option if you always want to send accept acknowledgments.</span></span><br /><span data-ttu-id="80903-138">-   **NE**。</span><span class="sxs-lookup"><span data-stu-id="80903-138">-   **NE**.</span></span> <span data-ttu-id="80903-139">選取此選項，如果您不想要傳送接受通知。</span><span class="sxs-lookup"><span data-stu-id="80903-139">Select this option if you never want to send accept acknowledgments.</span></span><br /><span data-ttu-id="80903-140">-   **SU**。</span><span class="sxs-lookup"><span data-stu-id="80903-140">-   **SU**.</span></span> <span data-ttu-id="80903-141">選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。</span><span class="sxs-lookup"><span data-stu-id="80903-141">Select this option if you want to send accept acknowledgments after successful transmission of a message.</span></span><br /><span data-ttu-id="80903-142">-   **ER**。</span><span class="sxs-lookup"><span data-stu-id="80903-142">-   **ER**.</span></span> <span data-ttu-id="80903-143">如果您想要傳送，請選取此選項只會發生錯誤時接受通知。</span><span class="sxs-lookup"><span data-stu-id="80903-143">Select this option if you want to send accept acknowledgments only in the event of an error.</span></span>|  
    |<span data-ttu-id="80903-144">**MSH.16**</span><span class="sxs-lookup"><span data-stu-id="80903-144">**MSH.16**</span></span>|<span data-ttu-id="80903-145">選取此選項，從應用程式通知類型的通知覆寫下列選項：</span><span class="sxs-lookup"><span data-stu-id="80903-145">Select from the following options for an acknowledgment override for the application acknowledgment type:</span></span><br /><br /> <span data-ttu-id="80903-146">-   **AL**。</span><span class="sxs-lookup"><span data-stu-id="80903-146">-   **AL**.</span></span> <span data-ttu-id="80903-147">如果您一定想要傳送的應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="80903-147">Select this option if you always want to send application acknowledgments.</span></span><br /><span data-ttu-id="80903-148">-   **NE**。</span><span class="sxs-lookup"><span data-stu-id="80903-148">-   **NE**.</span></span> <span data-ttu-id="80903-149">如果您不想要傳送應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="80903-149">Select this option if you never want to send application acknowledgments.</span></span><br /><span data-ttu-id="80903-150">-   **SU**。</span><span class="sxs-lookup"><span data-stu-id="80903-150">-   **SU**.</span></span> <span data-ttu-id="80903-151">如果您想要將訊息傳輸成功之後傳送應用程式通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="80903-151">Select this option if you want to send application acknowledgments after successful transmission of a message.</span></span><br /><span data-ttu-id="80903-152">-   **ER**。</span><span class="sxs-lookup"><span data-stu-id="80903-152">-   **ER**.</span></span> <span data-ttu-id="80903-153">如果您想要傳送的應用程式通知只會發生錯誤時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="80903-153">Select this option if you want to send application acknowledgments only in the event of an error.</span></span>|  
  
2.  <span data-ttu-id="80903-154">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="80903-154">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80903-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="80903-155">See Also</span></span>  
 <span data-ttu-id="80903-156">[記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="80903-156">[Logging Configuration](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span></span>  
 <span data-ttu-id="80903-157">[訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="80903-157">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
[<span data-ttu-id="80903-158">作業記錄、訊息批次處理、驗證和通知設定</span><span class="sxs-lookup"><span data-stu-id="80903-158">Operational logging, message batching, validation and asknowledgment settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)