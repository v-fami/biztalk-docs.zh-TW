---
title: "步驟 7： 建立及設定來源合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8788a9c-ae6f-461b-82e5-f4276d1d5e0c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba84bd9a0ab8c6f7d5ccd24b27e90ef9c441b93
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-create-and-configure-a-source-party"></a><span data-ttu-id="60f3b-102">步驟 7： 建立及設定來源合作對象</span><span class="sxs-lookup"><span data-stu-id="60f3b-102">Step 7: Create and Configure a Source Party</span></span>
<span data-ttu-id="60f3b-103">在此步驟中，您可以建立與設定的來源合作對象，以及指定傳送埠，以啟用外寄訊息的訊息標頭轉換。</span><span class="sxs-lookup"><span data-stu-id="60f3b-103">In this step, you create and configure a source party, and assign send ports to enable message header transformations for the outgoing message.</span></span>  
  
### <a name="to-create-and-configure-a-source-party"></a><span data-ttu-id="60f3b-104">建立和設定來源合作對象</span><span class="sxs-lookup"><span data-stu-id="60f3b-104">To create and configure a source party</span></span>  
  
1.  <span data-ttu-id="60f3b-105">在 BizTalk 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-105">In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="60f3b-106">在**合作對象屬性**對話方塊中的，在 [名稱] 欄位中，型別**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-106">In the **Party Properties** dialog box, in the Name field, type **Tutorial_BatchSource**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="60f3b-107">您在此方塊中輸入的值是從原始的 FHS3.1[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次的訊息，FragmentedInboundBatch.txt。</span><span class="sxs-lookup"><span data-stu-id="60f3b-107">The value that you type in this box is from FHS3.1 of the original [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batched message, FragmentedInboundBatch.txt.</span></span>  
  
3.  <span data-ttu-id="60f3b-108">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-108">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="60f3b-109">在 [傳送埠] 窗格的 [名稱] 欄位中，選取**Tutorial_2wayAck**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-109">In the Send Ports pane, for the Name field, select **Tutorial_2wayAck**.</span></span>  
  
5.  <span data-ttu-id="60f3b-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-110">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="60f3b-111">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-111">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
7.  <span data-ttu-id="60f3b-112">BTAHL7 組態總管] 中，在上**合作對象**索引標籤上，按一下 [ **Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-112">In BTAHL7 Configuration Explorer, on the **Parties** tab, click **Tutorial_BatchSource**.</span></span>  
  
8.  <span data-ttu-id="60f3b-113">選取**批次定義**BTAHL7 Configuration 總管索引標籤。</span><span class="sxs-lookup"><span data-stu-id="60f3b-113">Select the **Batch Definition** tab of BTAHL7 Configuration Explorer.</span></span> <span data-ttu-id="60f3b-114">選取**是**如**片段所需**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-114">Select **Yes** for **Fragmentation Required**, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="60f3b-115">選取**通知**] 索引標籤。如**的通知類型**，選取**OriginalMode**，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="60f3b-115">Select the **Acknowledgment** tab. For **Acknowledgment Type**, select **OriginalMode**, and then click **Save**.</span></span>  
  
 <span data-ttu-id="60f3b-116">若要繼續[步驟 8： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="60f3b-116">Proceed to [Step 8: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md).</span></span>