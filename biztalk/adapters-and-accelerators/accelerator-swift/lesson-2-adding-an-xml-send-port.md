---
title: "第 2 課： 加入 XML 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06b110b911c8cba2dbc643928e8b97e3746935a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-an-xml-send-port"></a><span data-ttu-id="ee2b2-102">第 2 課： 加入 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="ee2b2-102">Lesson 2: Adding an XML Send Port</span></span>
<span data-ttu-id="ee2b2-103">您可以使用傳送埠定義您想要傳送的訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-103">You use a send port to define how you want the messages sent.</span></span> <span data-ttu-id="ee2b2-104">在這一課，您可以建立傳送埠，以便定義傳送 XML 訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-104">In this lesson, you create a send port to define how XML messages should be sent.</span></span>  
  
### <a name="to-add-an-xml-send-port"></a><span data-ttu-id="ee2b2-105">若要加入 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="ee2b2-105">To add an XML send port</span></span>  
  
1.  <span data-ttu-id="ee2b2-106">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-106">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="ee2b2-107">在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_XML_SendPort**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-107">In the Send Port Properties dialog box, in the **Name** box, type **MT103_XML_SendPort**.</span></span>  
  
3.  <span data-ttu-id="ee2b2-108">在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-108">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="ee2b2-109">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-109">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="ee2b2-110">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-110">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="ee2b2-111">在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機 >: \Labs\Outbound**資料夾，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-111">In the Browse For Folder dialog box, move to the **\<drive>:\Labs\Outbound** folder, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ee2b2-112">在 [FILE 傳輸屬性] 對話方塊中，確定**%MessageID%.xml**輸入**檔案名稱**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-112">In the FILE Transport Properties dialog box, ensure that **%MessageID%.xml** is entered in the **File Name** box, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="ee2b2-113">在 [傳送埠屬性] 對話方塊中，確定**[biztalkserverapplication]**選取**傳送處理常式**中，且**PassThruTransmit**選取**傳送管線**方塊。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-113">In the Send Port Properties dialog box, ensure that **BizTalkServerApplication** is selected for the **Send handler** box, and that **PassThruTransmit** is selected for the **Send pipeline** box.</span></span>  
  
9. <span data-ttu-id="ee2b2-114">在左窗格中，按一下 **篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ee2b2-114">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="ee2b2-115">使用</span><span class="sxs-lookup"><span data-stu-id="ee2b2-115">Use this</span></span>|<span data-ttu-id="ee2b2-116">動作</span><span class="sxs-lookup"><span data-stu-id="ee2b2-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ee2b2-117">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-117">**Property**</span></span>|<span data-ttu-id="ee2b2-118">選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-118">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="ee2b2-119">**運算子**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-119">**Operator**</span></span>|<span data-ttu-id="ee2b2-120">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-120">Select **==**.</span></span>|  
    |<span data-ttu-id="ee2b2-121">**值**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-121">**Value**</span></span>|<span data-ttu-id="ee2b2-122">型別**MT103_FlatFile_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-122">Type **MT103_FlatFile_ReceivePort**.</span></span>|  
    |<span data-ttu-id="ee2b2-123">**群組**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-123">**Group**</span></span>|<span data-ttu-id="ee2b2-124">選取**和**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-124">Select **And**.</span></span>|  
  
10. <span data-ttu-id="ee2b2-125">按一下 下一步屬性列內部，執行下列：</span><span class="sxs-lookup"><span data-stu-id="ee2b2-125">Click inside the next property line and do the following:</span></span>  
  
    |<span data-ttu-id="ee2b2-126">使用</span><span class="sxs-lookup"><span data-stu-id="ee2b2-126">Use this</span></span>|<span data-ttu-id="ee2b2-127">動作</span><span class="sxs-lookup"><span data-stu-id="ee2b2-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ee2b2-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-128">**Property**</span></span>|<span data-ttu-id="ee2b2-129">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-129">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span></span>|  
    |<span data-ttu-id="ee2b2-130">**運算子**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-130">**Operator**</span></span>|<span data-ttu-id="ee2b2-131">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-131">Select **==**.</span></span>|  
    |<span data-ttu-id="ee2b2-132">**值**</span><span class="sxs-lookup"><span data-stu-id="ee2b2-132">**Value**</span></span>|<span data-ttu-id="ee2b2-133">型別**False**有效的訊息。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-133">Type **False** for valid messages.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ee2b2-134">您將加入**"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"**篩選運算式子句，讓傳送埠傳送僅成功剖析及驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-134">You add the **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False"** filter expression clause so that the send port sends only successfully parsed and validated messages.</span></span> <span data-ttu-id="ee2b2-135">不同於接收管線中使用原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解譯[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解譯器不會擱置失敗 （錯誤） 的訊息，但改為將其發佈至 MessageBox 和標記為失敗，將使用升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-135">Unlike a receive pipeline using native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] disassemblers, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] disassembler will not suspend a failed (erroneous) message, but instead publishes it to the MessageBox and marks it as failed, using promoted properties.</span></span> <span data-ttu-id="ee2b2-136">A4SWIFT 附加失敗的訊息發佈到 MessageBox 之前收集到的錯誤的 XML 表示法。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-136">A4SWIFT attaches an XML representation of the errors that were collected to the failed message before publishing it to the MessageBox.</span></span>  
    > <span data-ttu-id="ee2b2-137">不包括"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed = = False"篩選運算式子句中，您的傳送埠會將傳送所有訊息： 成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-137">Without including the "Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False" filter expression clause, your send port will send all messages: passed or failed.</span></span> <span data-ttu-id="ee2b2-138">如需失敗的訊息訂閱的詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-138">For more information about failed message subscriptions, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  
  
11. <span data-ttu-id="ee2b2-139">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-139">Click **Apply**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="ee2b2-140">在 BizTalk Server 管理主控台中，在**傳送埠**，以滑鼠右鍵按一下**MT103_XML_SendPort**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-140">In the BizTalk Server Administration Console, in **Send Ports**, right-click **MT103_XML_SendPort**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="ee2b2-141">若要繼續[模組 6： 部署商務規則](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="ee2b2-141">Proceed to [Module 6: Deploying the Business Rules](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).</span></span>