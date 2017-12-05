---
title: "Interrogative 教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 642f2521917dd87b60ee43a4cd7decaeeb1f1365
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="interrogative-tutorial"></a><span data-ttu-id="ce430-102">Interrogative 教學課程</span><span class="sxs-lookup"><span data-stu-id="ce430-102">Interrogative Tutorial</span></span>
<span data-ttu-id="ce430-103">本教學課程包含詳細的步驟，說明如何使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序中查詢/回應實例。</span><span class="sxs-lookup"><span data-stu-id="ce430-103">This tutorial contains detailed steps that describe how you use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a Query/Response scenario.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce430-104">若要使用此教學課程中，您必須安裝 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="ce430-104">To use this tutorial, you must install the MLLP test tools.</span></span> <span data-ttu-id="ce430-105">典型安裝 BTAHL7 不會安裝這些工具。</span><span class="sxs-lookup"><span data-stu-id="ce430-105">These tools are not installed by a Typical installation of BTAHL7.</span></span> <span data-ttu-id="ce430-106">您必須執行自訂安裝，然後選取**MLLP 測試工具**從配接器資料夾和**測試執行個體**從 [成品] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce430-106">You must run a Custom installation and select **MLLP Test Tool** from the Adapter folder and **Test Instances** from the Artifacts folder.</span></span> <span data-ttu-id="ce430-107">如果安裝測試工具，則系統將會包含資料夾\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。</span><span class="sxs-lookup"><span data-stu-id="ce430-107">If the test tools are installed, your system will contain the folder \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.</span></span> <span data-ttu-id="ce430-108">請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="ce430-108">See [install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="interrogative-scenario"></a><span data-ttu-id="ce430-109">Interrogative 案例</span><span class="sxs-lookup"><span data-stu-id="ce430-109">Interrogative Scenario</span></span>  
 <span data-ttu-id="ce430-110">本教學課程使用的查詢/回應或 Interrogative 案例。</span><span class="sxs-lookup"><span data-stu-id="ce430-110">This tutorial uses the Query/Response or Interrogative scenario.</span></span> <span data-ttu-id="ce430-111">在此案例中，商務流程是類似於下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ce430-111">In this scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="ce430-112">圖例之後已編號的清單描述工作流程。</span><span class="sxs-lookup"><span data-stu-id="ce430-112">The numbered list following the figure describes the workflow.</span></span>  
  
 <span data-ttu-id="ce430-113">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")</span><span class="sxs-lookup"><span data-stu-id="ce430-113">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")</span></span>  
  
1.  <span data-ttu-id="ce430-114">當許可放電和傳輸 (ADT) 的系統會將查詢傳送至醫院資訊系統時，就會開始工作流程。</span><span class="sxs-lookup"><span data-stu-id="ce430-114">The workflow begins when an Admissions Discharge and Transfer (ADT) system sends a query to the Hospital Information System.</span></span> <span data-ttu-id="ce430-115">HL7 訊息使用"**QRY ^ Q01**」 結構描述。</span><span class="sxs-lookup"><span data-stu-id="ce430-115">The HL7 message uses the "**QRY^Q01**" schema.</span></span> <span data-ttu-id="ce430-116">教學課程中，MllpSend 公用程式會模擬 ADT 系統傳送查詢訊息至醫院資訊系統，透過 ADT BTAHL7 整合引擎接收埠。</span><span class="sxs-lookup"><span data-stu-id="ce430-116">In the tutorial, the MllpSend utility simulates the ADT system sending the query message to the Hospital Information System through the ADT receive port in the BTAHL7 Integration Engine.</span></span>  
  
2.  <span data-ttu-id="ce430-117">BTAHL7 整合引擎接收 ADT 系統查詢訊息，並驗證它。</span><span class="sxs-lookup"><span data-stu-id="ce430-117">The BTAHL7 Integration Engine receives the query message from the ADT system and validates it.</span></span> <span data-ttu-id="ce430-118">接著，BTAHL7 管線會傳送通知回 ADT。</span><span class="sxs-lookup"><span data-stu-id="ce430-118">Then, the BTAHL7 pipeline sends an acknowledgment back to ADT.</span></span>  
  
3.  <span data-ttu-id="ce430-119">BTAHL7 介面引擎處理的訊息，並再查詢訊息至 HIS 目的合作對象透過 HIS 的路由傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="ce430-119">The BTAHL7 Interface Engine processes the message, and then routes the query message to the HIS destination party through the HIS send port.</span></span>  
  
4.  <span data-ttu-id="ce430-120">從原始的查詢中接收通知之後, ADT 系統等候回應。</span><span class="sxs-lookup"><span data-stu-id="ce430-120">After receiving the acknowledgment from the original query, the ADT system waits for a response.</span></span> <span data-ttu-id="ce430-121">回應訊息回透過 HIS 醫院資訊系統傳送接收連接埠。</span><span class="sxs-lookup"><span data-stu-id="ce430-121">The Hospital Information System sends a response message back through the HIS receive port.</span></span> <span data-ttu-id="ce430-122">本教學課程，MllpSend 公用程式會模擬醫院資訊系統傳送回應訊息。</span><span class="sxs-lookup"><span data-stu-id="ce430-122">For this tutorial, the MllpSend utility simulates the Hospital Information System sending the response message.</span></span>  
  
5.  <span data-ttu-id="ce430-123">BTAHL7 介面引擎處理回應訊息，然後將它路由傳送至目的合作對象透過 ADT 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ce430-123">The BTAHL7 Interface Engine processes the response message and then routes it to the destination party through the ADT send port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce430-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="ce430-124">In this section</span></span>  
  
-   [<span data-ttu-id="ce430-125">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="ce430-125">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)  
  
-   [<span data-ttu-id="ce430-126">步驟 1：建立及部署通用標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="ce430-126">Step 1: Create and Deploy Common Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="ce430-127">步驟 2：建立 V2.4 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="ce430-127">Step 2: Create Common Schemas for V2.4</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)  
  
-   [<span data-ttu-id="ce430-128">步驟 3：建立及部署觸發程序事件 (訊息) 專案</span><span class="sxs-lookup"><span data-stu-id="ce430-128">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)  
  
-   [<span data-ttu-id="ce430-129">步驟 4：建立接收埠，以接受 ADT 查詢訊息</span><span class="sxs-lookup"><span data-stu-id="ce430-129">Step 4: Create the Receive Port for Accepting ADT Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)  
  
-   [<span data-ttu-id="ce430-130">步驟 5：建立接收埠，以接受 HIS 訊息</span><span class="sxs-lookup"><span data-stu-id="ce430-130">Step 5: Create the Receive Port for Accepting HIS Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)  
  
-   [<span data-ttu-id="ce430-131">步驟 6：建立傳送埠以傳遞查詢訊息</span><span class="sxs-lookup"><span data-stu-id="ce430-131">Step 6: Create a Send Port to Deliver Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)  
  
-   [<span data-ttu-id="ce430-132">步驟 7：建立傳送埠以傳遞回應訊息</span><span class="sxs-lookup"><span data-stu-id="ce430-132">Step 7: Create a Send Port to Deliver Response Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)  
  
-   [<span data-ttu-id="ce430-133">步驟 8：設定合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="ce430-133">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)  
  
-   [<span data-ttu-id="ce430-134">步驟 9：重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ce430-134">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)  
  
-   [<span data-ttu-id="ce430-135">步驟 10：驗證詢問式案例</span><span class="sxs-lookup"><span data-stu-id="ce430-135">Step 10: Verify the Interrogative Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-interrogative-scenario.md)  

## <a name="next-step"></a><span data-ttu-id="ce430-136">下一步</span><span class="sxs-lookup"><span data-stu-id="ce430-136">Next step</span></span>  
 [<span data-ttu-id="ce430-137">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="ce430-137">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)
  
## <a name="see-also"></a><span data-ttu-id="ce430-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce430-138">See Also</span></span>  
[<span data-ttu-id="ce430-139">開始使用 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="ce430-139">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)