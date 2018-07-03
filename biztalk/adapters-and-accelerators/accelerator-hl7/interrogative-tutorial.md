---
title: 詢問式教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92c832de8b6572e5ac70b79db1cbcc75d3812ea6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003199"
---
# <a name="interrogative-tutorial"></a><span data-ttu-id="9246c-102">詢問式教學課程</span><span class="sxs-lookup"><span data-stu-id="9246c-102">Interrogative Tutorial</span></span>
<span data-ttu-id="9246c-103">本教學課程包含詳細的步驟，說明您如何使用 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助查詢/回應案例中的商務程序。</span><span class="sxs-lookup"><span data-stu-id="9246c-103">This tutorial contains detailed steps that describe how you use Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a Query/Response scenario.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9246c-104">若要使用本教學課程中，您必須安裝 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="9246c-104">To use this tutorial, you must install the MLLP test tools.</span></span> <span data-ttu-id="9246c-105">典型安裝 BTAHL7 不會安裝這些工具。</span><span class="sxs-lookup"><span data-stu-id="9246c-105">These tools are not installed by a Typical installation of BTAHL7.</span></span> <span data-ttu-id="9246c-106">您必須執行自訂安裝，並選取**MLLP 測試工具**從配接器資料夾並**測試執行個體**從 [成品] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9246c-106">You must run a Custom installation and select **MLLP Test Tool** from the Adapter folder and **Test Instances** from the Artifacts folder.</span></span> <span data-ttu-id="9246c-107">如果已安裝的測試工具，您的系統將會包含資料夾\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。</span><span class="sxs-lookup"><span data-stu-id="9246c-107">If the test tools are installed, your system will contain the folder \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.</span></span> <span data-ttu-id="9246c-108">請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="9246c-108">See [install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="interrogative-scenario"></a><span data-ttu-id="9246c-109">詢問式案例</span><span class="sxs-lookup"><span data-stu-id="9246c-109">Interrogative Scenario</span></span>  
 <span data-ttu-id="9246c-110">本教學課程使用的查詢/回應或詢問式案例。</span><span class="sxs-lookup"><span data-stu-id="9246c-110">This tutorial uses the Query/Response or Interrogative scenario.</span></span> <span data-ttu-id="9246c-111">在此案例中，商務流程是類似下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9246c-111">In this scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="9246c-112">下圖的編號的清單描述的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9246c-112">The numbered list following the figure describes the workflow.</span></span>  
  
 <span data-ttu-id="9246c-113">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")</span><span class="sxs-lookup"><span data-stu-id="9246c-113">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")</span></span>  
  
1.  <span data-ttu-id="9246c-114">在工作流程開始，當許可出院和傳輸 (ADT) 系統會將查詢傳送至醫院資訊系統。</span><span class="sxs-lookup"><span data-stu-id="9246c-114">The workflow begins when an Admissions Discharge and Transfer (ADT) system sends a query to the Hospital Information System.</span></span> <span data-ttu-id="9246c-115">HL7 訊息使用"**QRY ^ Q01**」 結構描述。</span><span class="sxs-lookup"><span data-stu-id="9246c-115">The HL7 message uses the "**QRY^Q01**" schema.</span></span> <span data-ttu-id="9246c-116">在本教學課程，MllpSend 公用程式可模擬 ADT 查詢訊息傳送到醫院資訊系統透過 ADT 系統接收埠，BTAHL7 整合引擎中。</span><span class="sxs-lookup"><span data-stu-id="9246c-116">In the tutorial, the MllpSend utility simulates the ADT system sending the query message to the Hospital Information System through the ADT receive port in the BTAHL7 Integration Engine.</span></span>  
  
2.  <span data-ttu-id="9246c-117">BTAHL7 整合引擎會接收來自 ADT 系統的查詢訊息，並加以驗證。</span><span class="sxs-lookup"><span data-stu-id="9246c-117">The BTAHL7 Integration Engine receives the query message from the ADT system and validates it.</span></span> <span data-ttu-id="9246c-118">然後，BTAHL7 管線會將通知送回 ADT。</span><span class="sxs-lookup"><span data-stu-id="9246c-118">Then, the BTAHL7 pipeline sends an acknowledgment back to ADT.</span></span>  
  
3.  <span data-ttu-id="9246c-119">BTAHL7 介面引擎會處理訊息，然後查詢訊息至 HIS 目的地合作對象透過 HIS 的路由傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="9246c-119">The BTAHL7 Interface Engine processes the message, and then routes the query message to the HIS destination party through the HIS send port.</span></span>  
  
4.  <span data-ttu-id="9246c-120">從原始的查詢中接收通知之後, ADT 系統會等候回應。</span><span class="sxs-lookup"><span data-stu-id="9246c-120">After receiving the acknowledgment from the original query, the ADT system waits for a response.</span></span> <span data-ttu-id="9246c-121">回應訊息後 HIS 醫院資訊系統會傳送接收埠。</span><span class="sxs-lookup"><span data-stu-id="9246c-121">The Hospital Information System sends a response message back through the HIS receive port.</span></span> <span data-ttu-id="9246c-122">本教學課程中，MllpSend 公用程式會模擬醫院資訊系統傳送的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9246c-122">For this tutorial, the MllpSend utility simulates the Hospital Information System sending the response message.</span></span>  
  
5.  <span data-ttu-id="9246c-123">BTAHL7 介面引擎會處理回應訊息，並再將其路由至目的合作對象，透過 ADT 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9246c-123">The BTAHL7 Interface Engine processes the response message and then routes it to the destination party through the ADT send port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9246c-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="9246c-124">In this section</span></span>  
  
-   [<span data-ttu-id="9246c-125">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="9246c-125">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)  
  
-   [<span data-ttu-id="9246c-126">步驟 1：建立及部署通用標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="9246c-126">Step 1: Create and Deploy Common Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="9246c-127">步驟 2：建立 V2.4 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="9246c-127">Step 2: Create Common Schemas for V2.4</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)  
  
-   [<span data-ttu-id="9246c-128">步驟 3：建立及部署觸發程序事件 (訊息) 專案</span><span class="sxs-lookup"><span data-stu-id="9246c-128">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)  
  
-   [<span data-ttu-id="9246c-129">步驟 4：建立接收埠，以接受 ADT 查詢訊息</span><span class="sxs-lookup"><span data-stu-id="9246c-129">Step 4: Create the Receive Port for Accepting ADT Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)  
  
-   [<span data-ttu-id="9246c-130">步驟 5：建立接收埠，以接受 HIS 訊息</span><span class="sxs-lookup"><span data-stu-id="9246c-130">Step 5: Create the Receive Port for Accepting HIS Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)  
  
-   [<span data-ttu-id="9246c-131">步驟 6：建立傳送埠以傳遞查詢訊息</span><span class="sxs-lookup"><span data-stu-id="9246c-131">Step 6: Create a Send Port to Deliver Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)  
  
-   [<span data-ttu-id="9246c-132">步驟 7：建立傳送埠以傳遞回應訊息</span><span class="sxs-lookup"><span data-stu-id="9246c-132">Step 7: Create a Send Port to Deliver Response Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)  
  
-   [<span data-ttu-id="9246c-133">步驟 8：設定合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="9246c-133">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)  
  
-   [<span data-ttu-id="9246c-134">步驟 9：重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9246c-134">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)  
  
-   [<span data-ttu-id="9246c-135">步驟 10：驗證詢問式案例</span><span class="sxs-lookup"><span data-stu-id="9246c-135">Step 10: Verify the Interrogative Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-interrogative-scenario.md)  

## <a name="next-step"></a><span data-ttu-id="9246c-136">下一步</span><span class="sxs-lookup"><span data-stu-id="9246c-136">Next step</span></span>  
 [<span data-ttu-id="9246c-137">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="9246c-137">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)
  
## <a name="see-also"></a><span data-ttu-id="9246c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9246c-138">See Also</span></span>  
[<span data-ttu-id="9246c-139">開始使用 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="9246c-139">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)