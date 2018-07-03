---
title: 步驟 4： 設定來源合作對象建立批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbb4e172c88c179ea53f1e48d1e08dcb63458607
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999823"
---
# <a name="step-4-configure-the-source-party-for-the-create-batch-scenario"></a><span data-ttu-id="530d9-102">步驟 4： 設定來源合作對象建立批次案例</span><span class="sxs-lookup"><span data-stu-id="530d9-102">Step 4: Configure the Source Party for the Create-Batch Scenario</span></span>
<span data-ttu-id="530d9-103">在此步驟中，您可以設定建立批次案例的來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="530d9-103">In this step, you configure the source party for the Create-Batch scenario.</span></span> <span data-ttu-id="530d9-104">您也選取通知，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會批次處理，此合作對象定義。</span><span class="sxs-lookup"><span data-stu-id="530d9-104">You also select the acknowledgments that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will batch, as defined for this party.</span></span> <span data-ttu-id="530d9-105">您可以設定通知批次的排程，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]之後的訊息計數達到 2 會建立批次。</span><span class="sxs-lookup"><span data-stu-id="530d9-105">You set the scheduling for the acknowledgment batch such that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will create the batch after the message count reaches 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="530d9-106">在此案例中，您會使用相同來源合作對象中建立[步驟 7： 建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)的本教學課程 （分散的輸入批次的案例） 的第 1 部分。</span><span class="sxs-lookup"><span data-stu-id="530d9-106">In this scenario, you use the same source party that you created in [Step 7: Create and Configure a Source Party](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md) of Part 1 of this tutorial (the Fragmented Inbound Batch Scenario).</span></span>  
  
### <a name="to-configure-the-source-party-for-the-create-batch-scenario"></a><span data-ttu-id="530d9-107">若要設定的來源合作對象建立批次案例</span><span class="sxs-lookup"><span data-stu-id="530d9-107">To configure the source party for the Create-Batch scenario</span></span>  
  
1. <span data-ttu-id="530d9-108">BTAHL7 設定總管 中，在**合作對象**索引標籤上的主控台樹狀目錄中，按一下**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="530d9-108">In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchSource**.</span></span>  
  
2. <span data-ttu-id="530d9-109">按一下 **通知**詳細資料窗格中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="530d9-109">Click the **Acknowledgment** tab in the Details pane.</span></span> <span data-ttu-id="530d9-110">確認**的通知類型**是**OriginalMode**。</span><span class="sxs-lookup"><span data-stu-id="530d9-110">Verify that the **Acknowledgment type** is **OriginalMode**.</span></span>  
  
3. <span data-ttu-id="530d9-111">按一下 [**批次定義**] 索引標籤。底下**可用訊息的 Ack**，按一下**BTAHL7Schemas.ADT_A03_231_GLO_DEF**，按一下 [移動] 向右箭號 (**>>**) 將此結構描述新增至**選取訊息的 Ack**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="530d9-111">Click the **Batch Definition** tab. Under **Available Message Acks**, click **BTAHL7Schemas.ADT_A03_231_GLO_DEF**, click the Move to the right arrow (**>>**) to add this schema to **Selected Message Acks**, and then click **Save**.</span></span>  
  
4. <span data-ttu-id="530d9-112">按一下 [**批次排程**] 索引標籤。在 [**重複批次之後**區段中，選取**訊息**，然後輸入**2**中**訊息**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="530d9-112">Click the **Batch Schedule** tab. In the **Repeat Batch After** section, select **Messages**, and then type **2** in the **Messages** box.</span></span>  
  
5. <span data-ttu-id="530d9-113">按一下 **啟動排程**。</span><span class="sxs-lookup"><span data-stu-id="530d9-113">Click **Start Schedule**.</span></span>  
  
   <span data-ttu-id="530d9-114">請繼續進行[步驟 5： 建立訊息批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="530d9-114">Proceed to [Step 5: Create the Send Port for the Message Batch](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md).</span></span>