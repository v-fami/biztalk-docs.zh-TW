---
title: 步驟 8A： 設定 ADT 系統的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0d750c2-a3c6-4571-a4e1-0d0aaaa4d400
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c1a608571c9cc3f939f9387c2e3a113273af554
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969759"
---
# <a name="step-8a-configure-party-information-for-the-adt-system"></a><span data-ttu-id="d5508-102">步驟 8A： 設定 ADT 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="d5508-102">Step 8A: Configure Party Information for the ADT System</span></span>
<span data-ttu-id="d5508-103">在此步驟中，您可以設定 ADT 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="d5508-103">In this step, you configure the party information for the ADT System.</span></span>  
  
### <a name="to-configure-the-adt-system-party-information"></a><span data-ttu-id="d5508-104">若要設定 ADT 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="d5508-104">To configure the ADT System party information</span></span>  
  
1. <span data-ttu-id="d5508-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d5508-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2. <span data-ttu-id="d5508-106">在 [合作對象屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_ADTSystem**。</span><span class="sxs-lookup"><span data-stu-id="d5508-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_ADTSystem**.</span></span> <span data-ttu-id="d5508-107">（您在此方塊中輸入的值是從原始 HL7 訊息的執行個體，ADT^A03.txt MSH3）。</span><span class="sxs-lookup"><span data-stu-id="d5508-107">(The value you type in this box is from the original HL7 message instance, ADT^A03.txt MSH3.)</span></span>  
  
3. <span data-ttu-id="d5508-108">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d5508-108">In the console tree, click **Send Ports**.</span></span>  
  
4. <span data-ttu-id="d5508-109">在 傳送埠 窗格中，按一下 中的空白欄位**名稱**欄中，選取**Tutorial_sendAck_ADT**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d5508-109">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendAck_ADT**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="d5508-110">按一下 **開始**，指向**程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。</span><span class="sxs-lookup"><span data-stu-id="d5508-110">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6. <span data-ttu-id="d5508-111">在 BTAHL7 設定總管 中，選取**通知** 索引標籤。針對**的通知類型**，選取**EnhancedMode**。</span><span class="sxs-lookup"><span data-stu-id="d5508-111">In the BTAHL7 Configuration Explorer, select the **Acknowledgment** tab. For **Acknowledgment type**, select **EnhancedMode**.</span></span>  
  
7. <span data-ttu-id="d5508-112">按一下 **儲存**，然後關閉 BTAHL7 設定總管。</span><span class="sxs-lookup"><span data-stu-id="d5508-112">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
   <span data-ttu-id="d5508-113">請繼續進行[步驟 8B： 設定 RX 系統的合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md)。</span><span class="sxs-lookup"><span data-stu-id="d5508-113">Proceed to [Step 8B: Configure Party Information for the RX System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md).</span></span>