---
title: "步驟 3： 建立及設定目的合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8746f115-9f69-4593-9943-9ccda45cd900
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d955aeaabe4d7207a07827de04c1c21e4c2c7a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-configure-a-destination-party"></a><span data-ttu-id="6b15b-102">步驟 3： 建立及設定目的合作對象</span><span class="sxs-lookup"><span data-stu-id="6b15b-102">Step 3: Create and Configure a Destination Party</span></span>
<span data-ttu-id="6b15b-103">在此步驟中，您可以建立並設定建立批次案例的目的合作對象。</span><span class="sxs-lookup"><span data-stu-id="6b15b-103">In this step, you create and configure a destination party for the Create-Batch scenario.</span></span> <span data-ttu-id="6b15b-104">您也可以選取訊息的[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]批次和批次排程時，針對該合作對象所定義。</span><span class="sxs-lookup"><span data-stu-id="6b15b-104">You also select the messages that [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] batches and the batch schedules, as defined for that party.</span></span> <span data-ttu-id="6b15b-105">您會排程批次傳送時間為一小時之後將檔案複製到資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b15b-105">You schedule the batch send time as one hour after copying the files into the folder.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6b15b-106">批次的頻率為一小時之後收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="6b15b-106"> batches any messages received thereafter with a frequency of one hour.</span></span>  
  
### <a name="to-create-and-configure-a-destination-party"></a><span data-ttu-id="6b15b-107">建立和設定目的地合作對象</span><span class="sxs-lookup"><span data-stu-id="6b15b-107">To create and configure a destination party</span></span>  
  
1.  <span data-ttu-id="6b15b-108">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-108">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="6b15b-109">在 合作對象屬性 對話方塊中**名稱**方塊中，輸入**Tutorial_BatchDest**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-109">In the Party Properties dialog box, in the **Name** box, type **Tutorial_BatchDest**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6b15b-110">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-110">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
4.  <span data-ttu-id="6b15b-111">BTAHL7 組態總管] 中，在上**合作對象**在主控台樹狀目錄索引標籤上，按一下 [ **Tutorial_BatchDest**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-111">In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchDest**.</span></span>  
  
5.  <span data-ttu-id="6b15b-112">按一下**通知**詳細資料窗格中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6b15b-112">Click the **Acknowledgment** tab in the Details pane.</span></span> <span data-ttu-id="6b15b-113">確認**的通知類型**是**無**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-113">Verify that the **Acknowledgment type** is **None**.</span></span>  
  
6.  <span data-ttu-id="6b15b-114">按一下**批次定義** 索引標籤。在**可用訊息**窗格中，選取**BTAHL7Schemas.ADT_A03_231_GLO_DEF**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-114">Click the **Batch Definition** tab. In the **Available Messages** pane, select **BTAHL7Schemas.ADT_A03_231_GLO_DEF**.</span></span> <span data-ttu-id="6b15b-115">按一下 移動 向右箭號 (**>>**) 新增到此結構描述**選取訊息**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-115">Click the Move to the right arrow (**>>**) to add this schema to **Selected Messages**, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="6b15b-116">按一下**批次排程** 索引標籤。在**重複批次之後**區段中，確認**小時**已選取，然後輸入**1**中**小時**方塊。</span><span class="sxs-lookup"><span data-stu-id="6b15b-116">Click the **Batch Schedule** tab. In the **Repeat Batch After** section, verify that **Hours** is selected, and then type **1** in the **Hours** box.</span></span> <span data-ttu-id="6b15b-117">在**第一個批次之前的小時**方塊中，輸入**1**，然後按一下 **啟動排程**。</span><span class="sxs-lookup"><span data-stu-id="6b15b-117">In the **Hours before first batch** box, type **1**, and then click **Start Schedule**.</span></span>  
  
 <span data-ttu-id="6b15b-118">若要繼續[步驟 4： 設定建立批次案例的來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="6b15b-118">Proceed to [Step 4: Configure the Source Party for the Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md).</span></span>