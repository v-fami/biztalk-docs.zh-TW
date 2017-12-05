---
title: "步驟 8B： 設定合作對象資訊 RX 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0b34ec9-220d-4a6b-9712-54c8099b663b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce204ed2e892a6206f6e2db28bbccd0201e2f0f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-8b-configure-party-information-for-the-rx-system"></a><span data-ttu-id="a5f8d-102">步驟 8B： 設定 RX 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="a5f8d-102">Step 8B: Configure Party Information for the RX System</span></span>
<span data-ttu-id="a5f8d-103">在此步驟中，您可以設定 RX 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-103">In this step, you configure the party information for the RX System.</span></span>  
  
### <a name="to-configure-the-rx-system-party-information"></a><span data-ttu-id="a5f8d-104">若要設定 RX 系統合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="a5f8d-104">To configure the RX System party information</span></span>  
  
1.  <span data-ttu-id="a5f8d-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="a5f8d-106">在 [合作對象屬性] 對話方塊中**名稱**方塊中，輸入**Tutorial_RXSystem**。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_RXSystem**.</span></span>  
  
3.  <span data-ttu-id="a5f8d-107">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-107">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="a5f8d-108">在 傳送埠 窗格中，按一下中的空白欄位**名稱**欄中，選取**Tutorial_sendMsg_RX**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-108">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendMsg_RX**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a5f8d-109">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="a5f8d-110">在 BTAHL7 組態總管 中，選取**MSH 對應**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a5f8d-110">In the BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="a5f8d-111">使用</span><span class="sxs-lookup"><span data-stu-id="a5f8d-111">Use this</span></span>|<span data-ttu-id="a5f8d-112">動作</span><span class="sxs-lookup"><span data-stu-id="a5f8d-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a5f8d-113">**MSH3**</span><span class="sxs-lookup"><span data-stu-id="a5f8d-113">**MSH3**</span></span>|<span data-ttu-id="a5f8d-114">型別**BTAHL7**左邊的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-114">Type **BTAHL7** in the left text box.</span></span>|  
    |<span data-ttu-id="a5f8d-115">**MSH5**</span><span class="sxs-lookup"><span data-stu-id="a5f8d-115">**MSH5**</span></span>|<span data-ttu-id="a5f8d-116">型別**Tutorial_RXSystem**左邊的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-116">Type **Tutorial_RXSystem** in the left text box.</span></span>|  
  
7.  <span data-ttu-id="a5f8d-117">按一下**儲存**，然後關閉 [總管] 中 BTAHL7 組態。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-117">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
 <span data-ttu-id="a5f8d-118">若要繼續[步驟 8 C： 設定合作對象資訊 HI 系統](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f8d-118">Proceed to [Step 8C: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md).</span></span>