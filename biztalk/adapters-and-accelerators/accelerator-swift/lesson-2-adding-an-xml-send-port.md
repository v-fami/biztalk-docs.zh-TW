---
title: 第 2 課： 新增 XML 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63d955b46ca007aea7ea74960e756520a82f43b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005327"
---
# <a name="lesson-2-adding-an-xml-send-port"></a><span data-ttu-id="a8273-102">第 2 課： 新增 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a8273-102">Lesson 2: Adding an XML Send Port</span></span>
<span data-ttu-id="a8273-103">您可以使用傳送埠定義您想要傳送的訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a8273-103">You use a send port to define how you want the messages sent.</span></span> <span data-ttu-id="a8273-104">在這一課，您可以建立傳送埠，以定義傳送 XML 訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a8273-104">In this lesson, you create a send port to define how XML messages should be sent.</span></span>  

### <a name="to-add-an-xml-send-port"></a><span data-ttu-id="a8273-105">若要新增 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a8273-105">To add an XML send port</span></span>  

1. <span data-ttu-id="a8273-106">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a8273-106">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="a8273-107">在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_XML_SendPort**。</span><span class="sxs-lookup"><span data-stu-id="a8273-107">In the Send Port Properties dialog box, in the **Name** box, type **MT103_XML_SendPort**.</span></span>  

3. <span data-ttu-id="a8273-108">在**傳輸**區段中，如**型別**方塊中，按一下下拉式清單中，並選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="a8273-108">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  

4. <span data-ttu-id="a8273-109">按一下 **設定**按鈕右邊的 類型 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a8273-109">Click the **Configure** button to the right of the Type drop-down list.</span></span>  

5. <span data-ttu-id="a8273-110">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="a8273-110">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  

6. <span data-ttu-id="a8273-111">在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs\Outbound**資料夾，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a8273-111">In the Browse For Folder dialog box, move to the **\<drive\>:\Labs\Outbound** folder, and then click **OK**.</span></span>  

7. <span data-ttu-id="a8273-112">在 [FILE 傳輸屬性] 對話方塊中，確定 **%MessageID%.xml**中輸入**檔名**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a8273-112">In the FILE Transport Properties dialog box, ensure that **%MessageID%.xml** is entered in the **File Name** box, and then click **OK**.</span></span>  

8. <span data-ttu-id="a8273-113">在傳送埠屬性 對話方塊中，請確認**BizTalkServerApplication**選取**傳送處理常式**中，且**PassThruTransmit**選取**傳送管線** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="a8273-113">In the Send Port Properties dialog box, ensure that **BizTalkServerApplication** is selected for the **Send handler** box, and that **PassThruTransmit** is selected for the **Send pipeline** box.</span></span>  

9. <span data-ttu-id="a8273-114">在左窗格中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a8273-114">In the left pane, click **Filters**, and then do the following:</span></span>  


   |   <span data-ttu-id="a8273-115">使用</span><span class="sxs-lookup"><span data-stu-id="a8273-115">Use this</span></span>   |              <span data-ttu-id="a8273-116">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a8273-116">To do this</span></span>              |
   |--------------|--------------------------------------|
   | <span data-ttu-id="a8273-117">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a8273-117">**Property**</span></span> |   <span data-ttu-id="a8273-118">選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="a8273-118">Select **BTS.ReceivePortName**.</span></span>    |
   | <span data-ttu-id="a8273-119">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="a8273-119">**Operator**</span></span> |            <span data-ttu-id="a8273-120">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="a8273-120">Select **==**.</span></span>            |
   |  <span data-ttu-id="a8273-121">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="a8273-121">**Value**</span></span>   | <span data-ttu-id="a8273-122">型別**MT103_FlatFile_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="a8273-122">Type **MT103_FlatFile_ReceivePort**.</span></span> |
   |  <span data-ttu-id="a8273-123">**群組**</span><span class="sxs-lookup"><span data-stu-id="a8273-123">**Group**</span></span>   |           <span data-ttu-id="a8273-124">選取 **和**。</span><span class="sxs-lookup"><span data-stu-id="a8273-124">Select **And**.</span></span>            |


10. <span data-ttu-id="a8273-125">按一下 [下一步] 的屬性列中並執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a8273-125">Click inside the next property line and do the following:</span></span>  

    |<span data-ttu-id="a8273-126">使用</span><span class="sxs-lookup"><span data-stu-id="a8273-126">Use this</span></span>|<span data-ttu-id="a8273-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a8273-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a8273-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a8273-128">**Property**</span></span>|<span data-ttu-id="a8273-129">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span><span class="sxs-lookup"><span data-stu-id="a8273-129">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span></span>|  
    |<span data-ttu-id="a8273-130">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="a8273-130">**Operator**</span></span>|<span data-ttu-id="a8273-131">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="a8273-131">Select **==**.</span></span>|  
    |<span data-ttu-id="a8273-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="a8273-132">**Value**</span></span>|<span data-ttu-id="a8273-133">型別**False**有效的訊息。</span><span class="sxs-lookup"><span data-stu-id="a8273-133">Type **False** for valid messages.</span></span>|  

    > [!NOTE]
    >  <span data-ttu-id="a8273-134">您將新增 **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"** 篩選運算式子句，讓傳送埠傳送僅成功剖析及驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a8273-134">You add the **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False"** filter expression clause so that the send port sends only successfully parsed and validated messages.</span></span> <span data-ttu-id="a8273-135">不同於接收管線中使用原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解譯器，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解譯器不會擱置失敗 （錯誤） 的訊息，但改為將其發佈到 MessageBox 和標記為失敗，使用 升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8273-135">Unlike a receive pipeline using native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] disassemblers, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] disassembler will not suspend a failed (erroneous) message, but instead publishes it to the MessageBox and marks it as failed, using promoted properties.</span></span> <span data-ttu-id="a8273-136">A4SWIFT 附加失敗的訊息發佈到 MessageBox 之前收集到的錯誤的 XML 表示法。</span><span class="sxs-lookup"><span data-stu-id="a8273-136">A4SWIFT attaches an XML representation of the errors that were collected to the failed message before publishing it to the MessageBox.</span></span>  
    > <span data-ttu-id="a8273-137">但不包括 「 Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"篩選運算式子句中，您的傳送埠會將傳送所有訊息： 成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="a8273-137">Without including the "Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False" filter expression clause, your send port will send all messages: passed or failed.</span></span> <span data-ttu-id="a8273-138">如需有關失敗的訊息的訂用帳戶的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="a8273-138">For more information about failed message subscriptions, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  

11. <span data-ttu-id="a8273-139">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a8273-139">Click **Apply**, and then click **OK**.</span></span>  

12. <span data-ttu-id="a8273-140">在 BizTalk Server 管理主控台中，在**傳送埠**，以滑鼠右鍵按一下**MT103_XML_SendPort**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="a8273-140">In the BizTalk Server Administration Console, in **Send Ports**, right-click **MT103_XML_SendPort**, and then click **Start**.</span></span>  

    <span data-ttu-id="a8273-141">請繼續進行[模組 6： 部署商務規則](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="a8273-141">Proceed to [Module 6: Deploying the Business Rules](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).</span></span>