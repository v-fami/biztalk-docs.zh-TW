---
title: "端對端 Tutorial1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: btahl7.endtoendtutorial
helpviewer_keywords:
- end-to-end tutorial, about the tutorial
- end-to-end tutorial
- tutorials, end-to-end tutorial
ms.assetid: 90625edc-70a0-42c9-a2fb-8eeb5465d766
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90dc31ac286f8ce1e38d9a511eb319828d8ae939
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="70469-102">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="70469-102">End-to-End Tutorial</span></span>
<span data-ttu-id="70469-103">本教學課程包含詳細的步驟，說明如何使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序在 「 訂閱者 」 和 「 發行者 」 的案例。</span><span class="sxs-lookup"><span data-stu-id="70469-103">This tutorial contains detailed steps that describe how you use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a subscriber and publisher scenario.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70469-104">若要使用此教學課程中，您必須在安裝 BTAHL7 時安裝測試工具。</span><span class="sxs-lookup"><span data-stu-id="70469-104">To use this tutorial, you must install the test tools when installing BTAHL7.</span></span> <span data-ttu-id="70469-105">如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。</span><span class="sxs-lookup"><span data-stu-id="70469-105">If you performed a typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="70469-106">在**自訂安裝**BTAHL7 自訂安裝，請選取畫面**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。</span><span class="sxs-lookup"><span data-stu-id="70469-106">At the **Custom Setup** screen of the BTAHL7 custom installation, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="70469-107">如需詳細資訊，請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="70469-107">For more information, see [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="declarative-scenario"></a><span data-ttu-id="70469-108">宣告式案例</span><span class="sxs-lookup"><span data-stu-id="70469-108">Declarative Scenario</span></span>  
 <span data-ttu-id="70469-109">本教學課程使用的發佈/訂閱或宣告式的案例。</span><span class="sxs-lookup"><span data-stu-id="70469-109">This tutorial uses the publish/subscribe or declarative scenario.</span></span> <span data-ttu-id="70469-110">在宣告式案例中，商務流程是類似於下圖所示。</span><span class="sxs-lookup"><span data-stu-id="70469-110">In the declarative scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="70469-111">圖例之後已編號的清單描述工作流程。</span><span class="sxs-lookup"><span data-stu-id="70469-111">The numbered list following the figure describes the workflow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")  
<span data-ttu-id="70469-112">下圖顯示的宣告式案例的商務流程</span><span class="sxs-lookup"><span data-stu-id="70469-112">Figure showing the flow of business for the declarative scenario</span></span>  
  
1.  <span data-ttu-id="70469-113">當 「 發行者 」，例如許可放電和傳輸系統會傳送訊息至特定的訂閱者時，就會開始工作流程。</span><span class="sxs-lookup"><span data-stu-id="70469-113">The workflow begins when the publisher, for example, an Admissions Discharge and Transfer system, sends a message to specific subscribers.</span></span> <span data-ttu-id="70469-114">工作流程中的 「 發行者 」 是 「 Tutorial_ADTSystem 」，並將訊息稱為 「**ADT ^ A103**。 」</span><span class="sxs-lookup"><span data-stu-id="70469-114">The publisher in the workflow is "Tutorial_ADTSystem", and the message is called "**ADT^A103**."</span></span>  
  
2.  <span data-ttu-id="70469-115">在訊息傳送給 BTAHL7 介面引擎，依次接收、 處理、 驗證、 重新格式化，並再將訊息路由至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="70469-115">The message is routed to the BTAHL7 Interface Engine, which in turn receives, processes, validates, reformats, and then routes the message to subscribers.</span></span>  
  
3.  <span data-ttu-id="70469-116">在此案例中的 「 訂閱者 」 為醫院資訊系統 (Tutorial_HISystem) 和藥局系統 (Tutorial_RXSystem)。</span><span class="sxs-lookup"><span data-stu-id="70469-116">The subscribers in this scenario are a Hospital Information System (Tutorial_HISystem) and a Pharmacy System (Tutorial_RXSystem).</span></span> <span data-ttu-id="70469-117">此案例使用檔案和 MLLP 配接器類型。</span><span class="sxs-lookup"><span data-stu-id="70469-117">This scenario uses both File and MLLP adapter types.</span></span> <span data-ttu-id="70469-118">不需要 「 發行者 」，這是要注意的訂閱者並 BTAHL7 適當地將傳送通知到 「 發行者 」 在處理訊息之後。</span><span class="sxs-lookup"><span data-stu-id="70469-118">The publisher does not need to be aware of the subscribers and BTAHL7 appropriately sends an acknowledgment to the publisher after processing the message.</span></span>  
  
4.  <span data-ttu-id="70469-119">「 發行者 」 傳送 ADT ^ A03 訊息透過單向 MLLP 配接器 (Tutorial_1WayReceivePort)。</span><span class="sxs-lookup"><span data-stu-id="70469-119">The publisher sends the ADT^A03 message through a one-way MLLP adapter (Tutorial_1WayReceivePort).</span></span>  
  
5.  <span data-ttu-id="70469-120">此訊息的目的地是 BTAHL7 介面引擎，讓內送訊息包含來源訊息 (MSH3 = Tutorial_ADTSystem) 和目的訊息 (MSH5 = BTAHL7InterfaceEngine)。</span><span class="sxs-lookup"><span data-stu-id="70469-120">The destination of this message is the BTAHL7 Interface Engine, so the incoming message contains a source message (MSH3 = Tutorial_ADTSystem) and a destination message (MSH5 = BTAHL7InterfaceEngine).</span></span>  
  
6.  <span data-ttu-id="70469-121">BTAHL7 產生通知 (ACK) 之後適當地驗證訊息，並接著會通知傳送給 Tutorial_ADTSystem 透過 File 配接器。</span><span class="sxs-lookup"><span data-stu-id="70469-121">BTAHL7 generates an acknowledgment (ACK) after appropriately validating the message, and then sends the acknowledgment to the Tutorial_ADTSystem through the File adapter.</span></span>  
  
7.  <span data-ttu-id="70469-122">Tutorial_HISystem 系統和 Tutorial_RXSystem 系統 BTAHL7 介面引擎所收到的 ADT 訊息來訂閱。</span><span class="sxs-lookup"><span data-stu-id="70469-122">The Tutorial_HISystem system and the Tutorial_RXSystem system subscribe to the ADT message received by the BTAHL7 Interface Engine.</span></span>  
  
8.  <span data-ttu-id="70469-123">當您使用指定的對應欄位的值時，就會發生轉換**MSH 對應**BTAHL7 組態總管 中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="70469-123">The transformation occurs when you specify values for the respective fields by using the **MSH Map** tab in BTAHL7 Configuration Explorer.</span></span>  
  
     <span data-ttu-id="70469-124">例如，合作對象 Tutorial_RXSystem 具有 MSH3 = BTHL7 中指定**MSH 對應** 索引標籤。因此，「 訂閱者 」 所收到的訊息會有"BTAHL7"做為 MSH3 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="70469-124">For example, the party Tutorial_RXSystem has MSH3=BTHL7 specified in the **MSH Map** tab. Therefore, the message received by the subscriber will have "BTAHL7" as the value for the MSH3 field.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70469-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="70469-125">In this section</span></span>  
  
-   [<span data-ttu-id="70469-126">測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="70469-126">Testing Your Installation</span></span>](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [<span data-ttu-id="70469-127">準備使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="70469-127">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [<span data-ttu-id="70469-128">步驟 1： 建立及部署標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="70469-128">Step 1: Create and Deploy Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="70469-129">步驟 2： 建立 v2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="70469-129">Step 2: Create Common Schemas for v2.3.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [<span data-ttu-id="70469-130">步驟 3： 建立專案並部署觸發程序事件 （訊息）</span><span class="sxs-lookup"><span data-stu-id="70469-130">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [<span data-ttu-id="70469-131">步驟 4： 建立接收埠，以便接受 ADT ^ A03 訊息從 ADT 系統使用 MLLP 配接器</span><span class="sxs-lookup"><span data-stu-id="70469-131">Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [<span data-ttu-id="70469-132">步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統</span><span class="sxs-lookup"><span data-stu-id="70469-132">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [<span data-ttu-id="70469-133">步驟 6： 建立傳送埠以傳送 ADT ^ A03 RX 系統使用 File 配接器的訊息</span><span class="sxs-lookup"><span data-stu-id="70469-133">Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [<span data-ttu-id="70469-134">步驟 7： 建立傳送埠以傳送 ADT ^ A03 他使用 MLLP 配接器的訊息</span><span class="sxs-lookup"><span data-stu-id="70469-134">Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [<span data-ttu-id="70469-135">步驟 8： 設定合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="70469-135">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [<span data-ttu-id="70469-136">步驟 9： 重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70469-136">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="70469-137">步驟 10： 確認端對端案例</span><span class="sxs-lookup"><span data-stu-id="70469-137">Step 10: Verify the End-to-End Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a><span data-ttu-id="70469-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70469-138">See also</span></span>
[<span data-ttu-id="70469-139">開始使用 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="70469-139">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)