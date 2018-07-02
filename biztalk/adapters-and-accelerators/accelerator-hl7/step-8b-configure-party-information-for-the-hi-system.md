---
title: 步驟 8B： 設定 HI 系統的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96338c05-1440-416e-a56a-6f5b19b55a60
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d2cfc31d4bc42b599d7403006f8b44a8bfab447
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973743"
---
# <a name="step-8b-configure-party-information-for-the-hi-system"></a><span data-ttu-id="b9f49-102">步驟 8B： 設定 HI 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="b9f49-102">Step 8B: Configure Party Information for the HI System</span></span>
<span data-ttu-id="b9f49-103">在此步驟中，您可以設定 HI 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="b9f49-103">In this step, you configure the party information for the HI System.</span></span>  
  
### <a name="to-configure-the-hi-system-party-information"></a><span data-ttu-id="b9f49-104">若要設定 HI 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="b9f49-104">To configure the HI System party information</span></span>  
  
1. <span data-ttu-id="b9f49-105">在 BizTalk 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="b9f49-105">In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="b9f49-106">在 [合作對象屬性] 對話方塊中，在**名稱**欄位中，輸入**HIS**。</span><span class="sxs-lookup"><span data-stu-id="b9f49-106">In the Party Properties dialog box, in the **Name** field, type **HIS**.</span></span> <span data-ttu-id="b9f49-107">（您在此方塊中輸入的值應該符合原始 HL7 訊息的執行個體，QRY^Q01.txt MSH5）。</span><span class="sxs-lookup"><span data-stu-id="b9f49-107">(The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH5.)</span></span>  
  
3. <span data-ttu-id="b9f49-108">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b9f49-108">In the Console Tree, click **Send Ports**.</span></span>  
  
4. <span data-ttu-id="b9f49-109">中**傳送埠**窗格中，如**名稱**在第一個資料列中，選取**HIS_Send**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b9f49-109">In the **Send Port** pane, for **Name** in the first row, select **HIS_Send**, and then click **OK**.</span></span>  
  
   <span data-ttu-id="b9f49-110">請繼續進行[步驟 9： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)。</span><span class="sxs-lookup"><span data-stu-id="b9f49-110">Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md).</span></span>