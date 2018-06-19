---
title: 步驟 8 C： 設定合作對象資訊 HI 系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ac5c113-7ee7-4009-8ca3-d263f74c7a8d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af1d853e381da6cbfbbe96fa805ca6396a1b7aae
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961066"
---
# <a name="step-8c-configure-party-information-for-the-hi-system"></a><span data-ttu-id="a2f4a-102">步驟 8 C： 設定 HI 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="a2f4a-102">Step 8C: Configure Party Information for the HI System</span></span>
<span data-ttu-id="a2f4a-103">在此步驟中，您可以設定 HI 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-103">In this step, you configure the party information for the HI System.</span></span>  
  
### <a name="to-configure-the-hi-system-party-information"></a><span data-ttu-id="a2f4a-104">若要設定 HI 系統合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="a2f4a-104">To configure the HI System party information</span></span>  
  
1.  <span data-ttu-id="a2f4a-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="a2f4a-106">在 [合作對象屬性] 對話方塊中**名稱**方塊中，輸入**Tutorial_HISystem**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_HISystem**.</span></span>  
  
3.  <span data-ttu-id="a2f4a-107">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-107">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="a2f4a-108">在 傳送埠 窗格中，按一下中的空白欄位**名稱**欄中，選取**Tutorial_MllpSend**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-108">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_MllpSend**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a2f4a-109">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="a2f4a-110">在 BTAHL7 組態總管 中，選取**MSH 對應**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a2f4a-110">In BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="a2f4a-111">使用</span><span class="sxs-lookup"><span data-stu-id="a2f4a-111">Use this</span></span>|<span data-ttu-id="a2f4a-112">動作</span><span class="sxs-lookup"><span data-stu-id="a2f4a-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a2f4a-113">**MSH3**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-113">**MSH3**</span></span>|<span data-ttu-id="a2f4a-114">型別**BTAHL7**， **IE**，和**UUID**中第一、 第二，和第三個訊息方塊中，分別。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-114">Type **BTAHL7**, **IE**, and **UUID** in the first, second, and third message boxes, respectively.</span></span>|  
    |<span data-ttu-id="a2f4a-115">**MSH5**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-115">**MSH5**</span></span>|<span data-ttu-id="a2f4a-116">型別**HI**，**系統**，和**GUID**中第一、 第二，和第三個訊息方塊中，分別。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-116">Type **HI**, **System**, and **GUID** in the first, second, and third message boxes, respectively.</span></span>|  
    |<span data-ttu-id="a2f4a-117">**MSH9**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-117">**MSH9**</span></span>|<span data-ttu-id="a2f4a-118">型別**ADT**和**A04**在第一個和第二個訊息方塊中，分別。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-118">Type **ADT** and **A04** in the first and second message boxes, respectively.</span></span>|  
    |<span data-ttu-id="a2f4a-119">**MSH12**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-119">**MSH12**</span></span>|<span data-ttu-id="a2f4a-120">型別**2.4**。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-120">Type **2.4**.</span></span>|  
    |<span data-ttu-id="a2f4a-121">**MSH15**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-121">**MSH15**</span></span>|<span data-ttu-id="a2f4a-122">選取**SU**之後成功傳輸訊息的傳送通知。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-122">Select **SU** to send acknowledgments after successful transmission of a message.</span></span>|  
    |<span data-ttu-id="a2f4a-123">**MSH16**</span><span class="sxs-lookup"><span data-stu-id="a2f4a-123">**MSH16**</span></span>|<span data-ttu-id="a2f4a-124">選取**NE**永遠不會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-124">Select **NE** to never send acknowledgments.</span></span>|  
  
7.  <span data-ttu-id="a2f4a-125">按一下**儲存**，然後關閉 [總管] 中 BTAHL7 組態。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-125">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2f4a-126">您不需要建立合作對象資訊 BTAHL7 介面引擎系統，因為不是此案例所需的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-126">You do not need to create party information for the BTAHL7 Interface Engine System, because configuration information is not required for this scenario.</span></span>  
  
 <span data-ttu-id="a2f4a-127">若要繼續[步驟 9： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-127">Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).</span></span>