---
title: 端對端 Tutorial1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.endtoendtutorial
helpviewer_keywords:
- end-to-end tutorial, about the tutorial
- end-to-end tutorial
- tutorials, end-to-end tutorial
ms.assetid: 90625edc-70a0-42c9-a2fb-8eeb5465d766
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 264a6eee008b9b327185c931ad4e5ac60cdc995a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000735"
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="1f266-102">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="1f266-102">End-to-End Tutorial</span></span>
<span data-ttu-id="1f266-103">本教學課程包含詳細的步驟，說明您如何使用 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序，在 「 訂閱者 」 和 「 發行者 」 的案例。</span><span class="sxs-lookup"><span data-stu-id="1f266-103">This tutorial contains detailed steps that describe how you use Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a subscriber and publisher scenario.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f266-104">若要使用本教學課程中，您必須在安裝 BTAHL7 時安裝測試工具。</span><span class="sxs-lookup"><span data-stu-id="1f266-104">To use this tutorial, you must install the test tools when installing BTAHL7.</span></span> <span data-ttu-id="1f266-105">如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程中正常運作。</span><span class="sxs-lookup"><span data-stu-id="1f266-105">If you performed a typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="1f266-106">在**自訂安裝**BTAHL7 自訂安裝中，選取畫面**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1f266-106">At the **Custom Setup** screen of the BTAHL7 custom installation, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="1f266-107">如需詳細資訊，請參閱 <<c0> [ 安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="1f266-107">For more information, see [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="declarative-scenario"></a><span data-ttu-id="1f266-108">宣告式案例</span><span class="sxs-lookup"><span data-stu-id="1f266-108">Declarative Scenario</span></span>  
 <span data-ttu-id="1f266-109">本教學課程會使用發佈/訂閱或宣告式案例。</span><span class="sxs-lookup"><span data-stu-id="1f266-109">This tutorial uses the publish/subscribe or declarative scenario.</span></span> <span data-ttu-id="1f266-110">在宣告式案例中，商務流程是類似下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1f266-110">In the declarative scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="1f266-111">下圖的編號的清單描述的工作流程。</span><span class="sxs-lookup"><span data-stu-id="1f266-111">The numbered list following the figure describes the workflow.</span></span>  
  
 <span data-ttu-id="1f266-112">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")</span><span class="sxs-lookup"><span data-stu-id="1f266-112">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")</span></span>  
<span data-ttu-id="1f266-113">下圖顯示的宣告式案例的商務流程</span><span class="sxs-lookup"><span data-stu-id="1f266-113">Figure showing the flow of business for the declarative scenario</span></span>  
  
1.  <span data-ttu-id="1f266-114">在工作流程開始時的發行者，比方說，門診出院和傳輸系統，將訊息傳送給特定的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1f266-114">The workflow begins when the publisher, for example, an Admissions Discharge and Transfer system, sends a message to specific subscribers.</span></span> <span data-ttu-id="1f266-115">工作流程中的 「 發行者 」 是 「 Tutorial_ADTSystem"，並將訊息稱為 「**ADT ^ A103**。 」</span><span class="sxs-lookup"><span data-stu-id="1f266-115">The publisher in the workflow is "Tutorial_ADTSystem", and the message is called "**ADT^A103**."</span></span>  
  
2.  <span data-ttu-id="1f266-116">訊息會路由至 BTAHL7 介面引擎，其接著接收、 處理、 驗證、 重新格式化，並再將訊息路由至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1f266-116">The message is routed to the BTAHL7 Interface Engine, which in turn receives, processes, validates, reformats, and then routes the message to subscribers.</span></span>  
  
3.  <span data-ttu-id="1f266-117">在此案例中的 「 訂閱者 」 為醫院的資訊系統 (Tutorial_HISystem) 和 Pharmacy 系統 (Tutorial_RXSystem)。</span><span class="sxs-lookup"><span data-stu-id="1f266-117">The subscribers in this scenario are a Hospital Information System (Tutorial_HISystem) and a Pharmacy System (Tutorial_RXSystem).</span></span> <span data-ttu-id="1f266-118">此案例使用檔案和 MLLP 配接器類型。</span><span class="sxs-lookup"><span data-stu-id="1f266-118">This scenario uses both File and MLLP adapter types.</span></span> <span data-ttu-id="1f266-119">不需要 「 發行者 」，這是要注意的訂閱者並 BTAHL7 適當地將傳送通知給 「 發行者 」 處理訊息之後。</span><span class="sxs-lookup"><span data-stu-id="1f266-119">The publisher does not need to be aware of the subscribers and BTAHL7 appropriately sends an acknowledgment to the publisher after processing the message.</span></span>  
  
4.  <span data-ttu-id="1f266-120">「 發行者 」 傳送 ADT ^ 將 adt^a03 訊息透過單向的 MLLP 配接器 (Tutorial_1WayReceivePort)。</span><span class="sxs-lookup"><span data-stu-id="1f266-120">The publisher sends the ADT^A03 message through a one-way MLLP adapter (Tutorial_1WayReceivePort).</span></span>  
  
5.  <span data-ttu-id="1f266-121">此訊息的目的地是 BTAHL7 介面引擎，讓內送訊息包含來源訊息 (MSH3 = Tutorial_ADTSystem) 和目的訊息 (MSH5 = BTAHL7InterfaceEngine)。</span><span class="sxs-lookup"><span data-stu-id="1f266-121">The destination of this message is the BTAHL7 Interface Engine, so the incoming message contains a source message (MSH3 = Tutorial_ADTSystem) and a destination message (MSH5 = BTAHL7InterfaceEngine).</span></span>  
  
6.  <span data-ttu-id="1f266-122">BTAHL7 之後適當地驗證訊息，產生通知 (ACK)，然後將通知傳送至 File 配接器透過 Tutorial_ADTSystem。</span><span class="sxs-lookup"><span data-stu-id="1f266-122">BTAHL7 generates an acknowledgment (ACK) after appropriately validating the message, and then sends the acknowledgment to the Tutorial_ADTSystem through the File adapter.</span></span>  
  
7.  <span data-ttu-id="1f266-123">Tutorial_HISystem 系統和 Tutorial_RXSystem 系統訂閱接收 BTAHL7 介面引擎 ADT 訊息。</span><span class="sxs-lookup"><span data-stu-id="1f266-123">The Tutorial_HISystem system and the Tutorial_RXSystem system subscribe to the ADT message received by the BTAHL7 Interface Engine.</span></span>  
  
8.  <span data-ttu-id="1f266-124">當您使用指定的對應欄位的值時，就會發生轉換**MSH 對應**BTAHL7 設定總管中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1f266-124">The transformation occurs when you specify values for the respective fields by using the **MSH Map** tab in BTAHL7 Configuration Explorer.</span></span>  
  
     <span data-ttu-id="1f266-125">比方說，合作對象 Tutorial_RXSystem 有 MSH3 = 中指定的 BTHL7 **MSH 對應** 索引標籤。因此，「 訂閱者 」 所收到的訊息會有"BTAHL7 」 做為 MSH3 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="1f266-125">For example, the party Tutorial_RXSystem has MSH3=BTHL7 specified in the **MSH Map** tab. Therefore, the message received by the subscriber will have "BTAHL7" as the value for the MSH3 field.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f266-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="1f266-126">In this section</span></span>  
  
-   [<span data-ttu-id="1f266-127">測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="1f266-127">Testing Your Installation</span></span>](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [<span data-ttu-id="1f266-128">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="1f266-128">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [<span data-ttu-id="1f266-129">步驟 1：建立及部署標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="1f266-129">Step 1: Create and Deploy Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="1f266-130">步驟 2： 建立 v2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="1f266-130">Step 2: Create Common Schemas for v2.3.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [<span data-ttu-id="1f266-131">步驟 3：建立及部署觸發程序事件 (訊息) 專案</span><span class="sxs-lookup"><span data-stu-id="1f266-131">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [<span data-ttu-id="1f266-132">步驟 4：建立接收埠，以使用 MLLP 配接器接受來自 ADT 系統的 ADT^A03 訊息</span><span class="sxs-lookup"><span data-stu-id="1f266-132">Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [<span data-ttu-id="1f266-133">步驟 5：建立傳送埠，以使用 FILE 配接器將通知傳送到 ADT 系統</span><span class="sxs-lookup"><span data-stu-id="1f266-133">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [<span data-ttu-id="1f266-134">步驟 6：建立傳送埠，以使用 FILE 配接器將 ADT^A03 訊息傳遞給 RX 系統</span><span class="sxs-lookup"><span data-stu-id="1f266-134">Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [<span data-ttu-id="1f266-135">步驟 7：建立傳送埠，以使用 MLLP 配接器將 ADT^A03 訊息傳遞給 HIS</span><span class="sxs-lookup"><span data-stu-id="1f266-135">Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [<span data-ttu-id="1f266-136">步驟 8：設定合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="1f266-136">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [<span data-ttu-id="1f266-137">步驟 9：重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1f266-137">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="1f266-138">步驟 10：驗證端對端案例</span><span class="sxs-lookup"><span data-stu-id="1f266-138">Step 10: Verify the End-to-End Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a><span data-ttu-id="1f266-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f266-139">See also</span></span>
[<span data-ttu-id="1f266-140">開始使用 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="1f266-140">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)