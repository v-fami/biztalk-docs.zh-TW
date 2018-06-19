---
title: 步驟 1： 設定批次的批次中超出的合作對象資訊 |Microsoft 文件
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
ms.openlocfilehash: 4cb67fb2e1a232894a0e936bc7827270ca79e6f8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960508"
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a><span data-ttu-id="0aabe-102">步驟 1： 設定批次中的合作對象資訊/出批次</span><span class="sxs-lookup"><span data-stu-id="0aabe-102">Step 1: Configure Party Information for Batch In/Batch Out</span></span>
<span data-ttu-id="0aabe-103">在此步驟中，您關閉片段的合作對象啟用批次的批次中 / 出案例批次。</span><span class="sxs-lookup"><span data-stu-id="0aabe-103">In this step, you turn off fragmentation of batching for the party, enabling the Batch In/Batch Out scenario.</span></span> <span data-ttu-id="0aabe-104">然後重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來啟用組態變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="0aabe-104">You then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to enable the configuration change to take effect.</span></span>  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a><span data-ttu-id="0aabe-105">若要關閉的合作對象的批次片段</span><span class="sxs-lookup"><span data-stu-id="0aabe-105">To turn off fragmentation of batching for the party</span></span>  
  
1.  <span data-ttu-id="0aabe-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="0aabe-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
2.  <span data-ttu-id="0aabe-107">BTAHL7 組態總管 中，在上**合作對象**索引標籤的左窗格中，按一下**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="0aabe-107">In BTAHL7 Configuration Explorer, on the **Parties** tab in the left-hand pane, click **Tutorial_BatchSource**.</span></span>  
  
3.  <span data-ttu-id="0aabe-108">按一下**批次定義** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0aabe-108">Click the **Batch Definition** tab.</span></span>  
  
4.  <span data-ttu-id="0aabe-109">選取**否**如**片段所需**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="0aabe-109">Select **No** for **Fragmentation required**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="0aabe-110">請確定在**可復原交換支援所需**下拉式清單**False**已選取。</span><span class="sxs-lookup"><span data-stu-id="0aabe-110">Make sure that in **Recoverable Interchange Support Required** dropdown list **False** is selected.</span></span>  
  
 <span data-ttu-id="0aabe-111">若要繼續[步驟 2： 修改或建立傳送和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="0aabe-111">Proceed to [Step 2: Modify or Create the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span></span>