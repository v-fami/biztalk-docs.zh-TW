---
title: 在步驟 8A： 設定合作對象資訊 ADT System_hl7_main |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 693fda8b-9a99-4a6e-89b7-294f84676350
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9683fd02f94b96ead6817c72298338c064a14cc1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960636"
---
# <a name="step-8a-configure-party-information-for-the-adt-systemhl7main"></a><span data-ttu-id="9ceec-102">在步驟 8A： 設定 ADT System_hl7_main 合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="9ceec-102">Step 8A: Configure Party Information for the ADT System_hl7_main</span></span>
<span data-ttu-id="9ceec-103">在此步驟中，您可以設定 ADT 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="9ceec-103">In this step, you configure the party information for the ADT System.</span></span>  
  
### <a name="to-configure-the-adt-system-party-information"></a><span data-ttu-id="9ceec-104">若要設定 ADT 系統合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="9ceec-104">To configure the ADT System party information</span></span>  
  
1.  <span data-ttu-id="9ceec-105">在 BizTalk 管理主控台中，展開**BizTalk Server 管理**，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-105">In the BizTalk Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**.</span></span> <span data-ttu-id="9ceec-106">以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-106">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="9ceec-107">在 [合作對象屬性] 對話方塊中**名稱**欄位中，輸入**ADT**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-107">In the Party Properties dialog box, in the **Name** field, type **ADT**.</span></span> <span data-ttu-id="9ceec-108">（您在此方塊中輸入的值應該符合原始 HL7 訊息執行個體，QRY^Q01.txt MSH3）。</span><span class="sxs-lookup"><span data-stu-id="9ceec-108">(The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH3.)</span></span>  
  
3.  <span data-ttu-id="9ceec-109">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-109">In the Console Tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="9ceec-110">在**傳送埠**] 窗格中，針對**名稱**在第一個資料列中，選取**ADT_Send**，然後按一下 [ **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-110">In the **Send Port** pane, for **Name** in the first row, select **ADT_Send**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="9ceec-111">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-111">Click **Start**, point to **Programs**, point to **Microsoft  BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="9ceec-112">在 [BTAHL7 組態總管] 中，按一下 [**通知**] 索引標籤。如**的通知類型**，選取**EnhancedMode**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-112">In BTAHL7 Configuration Explorer, click the **Acknowledgment** tab. For **Acknowledgment Type**, select **EnhancedMode**.</span></span>  
  
7.  <span data-ttu-id="9ceec-113">在通知中的屬性 Inboiund 訊息 窗格中，針對**MSH15-接受的通知類型**，選取**AL**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-113">In the Acknowledgment Properties in Inboiund Message pane, for **MSH15 - Accept Acknowledgment Type**, select **AL**.</span></span>  
  
8.  <span data-ttu-id="9ceec-114">在通知屬性 窗格中，針對**MSH16-應用程式的通知類型**，選取**NE**。</span><span class="sxs-lookup"><span data-stu-id="9ceec-114">In the Acknowledgment Properties pane, for **MSH16 - Application Acknowledgment Type**, select **NE**.</span></span>  
  
9. <span data-ttu-id="9ceec-115">按一下**儲存**，然後關閉 BTAHL7 Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="9ceec-115">Click **Save**, and then close BTAHL7 Configuration Explorer.</span></span>  
  
 <span data-ttu-id="9ceec-116">若要繼續[步驟 8B： 設定合作對象資訊 HI 系統](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md)。</span><span class="sxs-lookup"><span data-stu-id="9ceec-116">Proceed to [Step 8B: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md).</span></span>