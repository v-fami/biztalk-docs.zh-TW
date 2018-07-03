---
title: 步驟 8c： 設定 HI 系統的合作對象資訊 |Microsoft Docs
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
ms.openlocfilehash: aba42674a78bbed850c0994ec23c477c36b29c2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970823"
---
# <a name="step-8c-configure-party-information-for-the-hi-system"></a><span data-ttu-id="4750f-102">步驟 8c： 設定 HI 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="4750f-102">Step 8C: Configure Party Information for the HI System</span></span>
<span data-ttu-id="4750f-103">在此步驟中，您可以設定 HI 系統的合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="4750f-103">In this step, you configure the party information for the HI System.</span></span>  

### <a name="to-configure-the-hi-system-party-information"></a><span data-ttu-id="4750f-104">若要設定 HI 系統的合作對象資訊</span><span class="sxs-lookup"><span data-stu-id="4750f-104">To configure the HI System party information</span></span>  

1. <span data-ttu-id="4750f-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="4750f-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="4750f-106">在 [合作對象屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_HISystem**。</span><span class="sxs-lookup"><span data-stu-id="4750f-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_HISystem**.</span></span>  

3. <span data-ttu-id="4750f-107">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="4750f-107">In the console tree, click **Send Ports**.</span></span>  

4. <span data-ttu-id="4750f-108">在 傳送埠 窗格中，按一下 中的空白欄位**名稱**欄中，選取**Tutorial_MllpSend**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4750f-108">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_MllpSend**, and then click **OK**.</span></span>  

5. <span data-ttu-id="4750f-109">按一下 **開始**，指向**程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。</span><span class="sxs-lookup"><span data-stu-id="4750f-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  

6. <span data-ttu-id="4750f-110">在 [BTAHL7 設定總管] 中，選取**MSH 對應**索引標籤，然後再執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4750f-110">In BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:</span></span>  


   | <span data-ttu-id="4750f-111">使用</span><span class="sxs-lookup"><span data-stu-id="4750f-111">Use this</span></span>  |                                             <span data-ttu-id="4750f-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="4750f-112">To do this</span></span>                                             |
   |-----------|----------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="4750f-113">**MSH3**</span><span class="sxs-lookup"><span data-stu-id="4750f-113">**MSH3**</span></span>  | <span data-ttu-id="4750f-114">型別**BTAHL7**， **IE**，並**UUID**第一次，第二個，，和第三個訊息方塊中，分別。</span><span class="sxs-lookup"><span data-stu-id="4750f-114">Type **BTAHL7**, **IE**, and **UUID** in the first, second, and third message boxes, respectively.</span></span> |
   | <span data-ttu-id="4750f-115">**MSH5**</span><span class="sxs-lookup"><span data-stu-id="4750f-115">**MSH5**</span></span>  | <span data-ttu-id="4750f-116">型別**HI**，**系統**，並**GUID**第一次，第二個，，和第三個訊息方塊中，分別。</span><span class="sxs-lookup"><span data-stu-id="4750f-116">Type **HI**, **System**, and **GUID** in the first, second, and third message boxes, respectively.</span></span> |
   | <span data-ttu-id="4750f-117">**MSH9**</span><span class="sxs-lookup"><span data-stu-id="4750f-117">**MSH9**</span></span>  |           <span data-ttu-id="4750f-118">型別**ADT**並**A04**在第一個和第二個訊息方塊中分別。</span><span class="sxs-lookup"><span data-stu-id="4750f-118">Type **ADT** and **A04** in the first and second message boxes, respectively.</span></span>            |
   | <span data-ttu-id="4750f-119">**MSH12**</span><span class="sxs-lookup"><span data-stu-id="4750f-119">**MSH12**</span></span> |                                           <span data-ttu-id="4750f-120">型別**2.4**。</span><span class="sxs-lookup"><span data-stu-id="4750f-120">Type **2.4**.</span></span>                                            |
   | <span data-ttu-id="4750f-121">**MSH15**</span><span class="sxs-lookup"><span data-stu-id="4750f-121">**MSH15**</span></span> |         <span data-ttu-id="4750f-122">選取  **SU**之後成功傳輸訊息的傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4750f-122">Select **SU** to send acknowledgments after successful transmission of a message.</span></span>          |
   | <span data-ttu-id="4750f-123">**MSH16**</span><span class="sxs-lookup"><span data-stu-id="4750f-123">**MSH16**</span></span> |                            <span data-ttu-id="4750f-124">選取  **NE**永遠不會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4750f-124">Select **NE** to never send acknowledgments.</span></span>                            |


7. <span data-ttu-id="4750f-125">按一下 **儲存**，然後關閉 BTAHL7 設定總管。</span><span class="sxs-lookup"><span data-stu-id="4750f-125">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="4750f-126">您不需要建立合作對象資訊 BTAHL7 介面引擎系統，因為並不需要在此案例的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="4750f-126">You do not need to create party information for the BTAHL7 Interface Engine System, because configuration information is not required for this scenario.</span></span>  

   <span data-ttu-id="4750f-127">請繼續進行[步驟 9： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4750f-127">Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).</span></span>