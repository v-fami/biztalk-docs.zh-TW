---
title: 步驟 1： 設定批次批次中外的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a93d774b-1282-40d9-836f-44abeb65f78e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eafe692cf86ccf3c6fbe0713c1e621a99a601d5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974919"
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a><span data-ttu-id="98526-102">步驟 1： 設定合作對象資訊中的批次/批次出</span><span class="sxs-lookup"><span data-stu-id="98526-102">Step 1: Configure Party Information for Batch In/Batch Out</span></span>
<span data-ttu-id="98526-103">在此步驟中，您關閉批次處理的合作對象，讓批次的片段中 / 批次出案例。</span><span class="sxs-lookup"><span data-stu-id="98526-103">In this step, you turn off fragmentation of batching for the party, enabling the Batch In/Batch Out scenario.</span></span> <span data-ttu-id="98526-104">然後重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]以便讓設定變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="98526-104">You then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to enable the configuration change to take effect.</span></span>  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a><span data-ttu-id="98526-105">若要關閉批次處理的合作對象的片段</span><span class="sxs-lookup"><span data-stu-id="98526-105">To turn off fragmentation of batching for the party</span></span>  
  
1. <span data-ttu-id="98526-106">按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下**BTAHL7 設定總管**。</span><span class="sxs-lookup"><span data-stu-id="98526-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
2. <span data-ttu-id="98526-107">BTAHL7 設定總管 中，在**合作對象**索引標籤的左窗格中，按一下**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="98526-107">In BTAHL7 Configuration Explorer, on the **Parties** tab in the left-hand pane, click **Tutorial_BatchSource**.</span></span>  
  
3. <span data-ttu-id="98526-108">按一下 [**批次定義**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="98526-108">Click the **Batch Definition** tab.</span></span>  
  
4. <span data-ttu-id="98526-109">選取**否**for**片段所需**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="98526-109">Select **No** for **Fragmentation required**, and then click **Save**.</span></span>  
  
5. <span data-ttu-id="98526-110">請確定在**可復原交換支援所需**下拉式清單中**False**已選取。</span><span class="sxs-lookup"><span data-stu-id="98526-110">Make sure that in **Recoverable Interchange Support Required** dropdown list **False** is selected.</span></span>  
  
   <span data-ttu-id="98526-111">請繼續進行[步驟 2： 修改或建立傳送和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="98526-111">Proceed to [Step 2: Modify or Create the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span></span>