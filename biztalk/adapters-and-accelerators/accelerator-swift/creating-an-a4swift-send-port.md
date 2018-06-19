---
title: 建立 A4SWIFT 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
ms.assetid: d1ee18f8-a6aa-4cd5-9e65-fb2e0fa2d0c2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf24cb99643acc869123450ce14fd5050ee7408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210246"
---
# <a name="creating-an-a4swift-send-port"></a><span data-ttu-id="f0253-102">建立 A4SWIFT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="f0253-102">Creating an A4SWIFT Send Port</span></span>
<span data-ttu-id="f0253-103">您必須建立傳送埠以啟用[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 網路時，傳送訊息，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f0253-103">You must create a send port to enable [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to send a message to the SWIFT network, as shown in the following figure.</span></span> <span data-ttu-id="f0253-104">此傳送埠會傳送至輸出檔案資料夾的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="f0253-104">This send port will send flat file messages to an outbound file folder.</span></span> <span data-ttu-id="f0253-105">此傳送埠被為了與 Message Repair 和 New Submission 功能運作。</span><span class="sxs-lookup"><span data-stu-id="f0253-105">This send port is designed to work with the Message Repair and New Submission feature.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-send-port-configuration.gif "A4SWIFT_Send_Port_Configuration")  
  
 <span data-ttu-id="f0253-106">**摘要**</span><span class="sxs-lookup"><span data-stu-id="f0253-106">**Summary**</span></span>  
  
 <span data-ttu-id="f0253-107">建立並啟動具有下列屬性和元件的靜態單向傳送埠：</span><span class="sxs-lookup"><span data-stu-id="f0253-107">Create and start a static one-way send port with the following properties and components:</span></span>  
  
|<span data-ttu-id="f0253-108">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="f0253-108">Property/Component</span></span>|<span data-ttu-id="f0253-109">設定</span><span class="sxs-lookup"><span data-stu-id="f0253-109">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="f0253-110">傳送埠</span><span class="sxs-lookup"><span data-stu-id="f0253-110">Send port</span></span>|<span data-ttu-id="f0253-111">靜態單向連接埠</span><span class="sxs-lookup"><span data-stu-id="f0253-111">Static one-way port</span></span>|  
|<span data-ttu-id="f0253-112">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="f0253-112">Transport type</span></span>|<span data-ttu-id="f0253-113">FILE</span><span class="sxs-lookup"><span data-stu-id="f0253-113">FILE</span></span>|  
|<span data-ttu-id="f0253-114">目的資料夾 (位址 URI)</span><span class="sxs-lookup"><span data-stu-id="f0253-114">Destination folder (Address URI)</span></span>|<span data-ttu-id="f0253-115">您想要從傳送訊息的資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="f0253-115">Name of the folder that you want to send messages from</span></span>|  
|<span data-ttu-id="f0253-116">檔案名稱 （位址的 URI）</span><span class="sxs-lookup"><span data-stu-id="f0253-116">File Name (Address URI)</span></span>|<span data-ttu-id="f0253-117">%MessageID%.txt</span><span class="sxs-lookup"><span data-stu-id="f0253-117">%MessageID%.txt</span></span>|  
|<span data-ttu-id="f0253-118">篩選</span><span class="sxs-lookup"><span data-stu-id="f0253-118">Filters</span></span>|<span data-ttu-id="f0253-119">下表中所述</span><span class="sxs-lookup"><span data-stu-id="f0253-119">As described in the table below</span></span>|  
  
### <a name="to-add-the-sent-port"></a><span data-ttu-id="f0253-120">新增傳送的埠</span><span class="sxs-lookup"><span data-stu-id="f0253-120">To add the sent port</span></span>  
  
1.  <span data-ttu-id="f0253-121">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f0253-121">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f0253-122">在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="f0253-122">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port.</span></span>  
  
3.  <span data-ttu-id="f0253-123">在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="f0253-123">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="f0253-124">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f0253-124">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="f0253-125">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="f0253-125">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="f0253-126">在 [瀏覽資料夾] 對話方塊中，移至您想要從傳送訊息的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0253-126">In the Browse For Folder dialog box, move to the folder that you want to send messages from.</span></span> <span data-ttu-id="f0253-127">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f0253-127">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0253-128">如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。</span><span class="sxs-lookup"><span data-stu-id="f0253-128">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
7.  <span data-ttu-id="f0253-129">在**檔案名稱**方塊中，輸入 **%MessageID%.txt**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f0253-129">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f0253-130">在**傳送埠屬性**對話方塊方塊中，按一下下拉式清單，如**傳送管線**] 方塊中，然後選取 [自訂傳送管線。</span><span class="sxs-lookup"><span data-stu-id="f0253-130">In the **Send Port Properties** dialog box, click the drop-down list for the **Send pipeline** box, and then select your custom send pipeline.</span></span>  
  
9. <span data-ttu-id="f0253-131">在左窗格中，按一下 **篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f0253-131">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="f0253-132">使用</span><span class="sxs-lookup"><span data-stu-id="f0253-132">Use this</span></span>|<span data-ttu-id="f0253-133">動作</span><span class="sxs-lookup"><span data-stu-id="f0253-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f0253-134">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f0253-134">**Property**</span></span>|<span data-ttu-id="f0253-135">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="f0253-135">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="f0253-136">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f0253-136">**Operator**</span></span>|<span data-ttu-id="f0253-137">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="f0253-137">Select **==**.</span></span>|  
    |<span data-ttu-id="f0253-138">**值**</span><span class="sxs-lookup"><span data-stu-id="f0253-138">**Value**</span></span>|<span data-ttu-id="f0253-139">型別**A4SWIFT_MRSRCompleted**。</span><span class="sxs-lookup"><span data-stu-id="f0253-139">Type **A4SWIFT_MRSRCompleted**.</span></span>|  
    |<span data-ttu-id="f0253-140">**群組**</span><span class="sxs-lookup"><span data-stu-id="f0253-140">**Group**</span></span>|<span data-ttu-id="f0253-141">選取**或者。**</span><span class="sxs-lookup"><span data-stu-id="f0253-141">Select **Or.**</span></span>|  
    |<span data-ttu-id="f0253-142">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f0253-142">**Property**</span></span>|<span data-ttu-id="f0253-143">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="f0253-143">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="f0253-144">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f0253-144">**Operator**</span></span>|<span data-ttu-id="f0253-145">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="f0253-145">Select **==**.</span></span>|  
    |<span data-ttu-id="f0253-146">**值**</span><span class="sxs-lookup"><span data-stu-id="f0253-146">**Value**</span></span>|<span data-ttu-id="f0253-147">型別**A4SWIFT_MRSRFailed**。</span><span class="sxs-lookup"><span data-stu-id="f0253-147">Type **A4SWIFT_MRSRFailed**.</span></span>|  
    |<span data-ttu-id="f0253-148">**群組**</span><span class="sxs-lookup"><span data-stu-id="f0253-148">**Group**</span></span>|<span data-ttu-id="f0253-149">選取**或**。</span><span class="sxs-lookup"><span data-stu-id="f0253-149">Select **Or**.</span></span>|  
    |<span data-ttu-id="f0253-150">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f0253-150">**Property**</span></span>|<span data-ttu-id="f0253-151">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**。</span><span class="sxs-lookup"><span data-stu-id="f0253-151">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span></span>|  
    |<span data-ttu-id="f0253-152">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f0253-152">**Operator**</span></span>|<span data-ttu-id="f0253-153">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="f0253-153">Select **==**.</span></span>|  
    |<span data-ttu-id="f0253-154">**值**</span><span class="sxs-lookup"><span data-stu-id="f0253-154">**Value**</span></span>|<span data-ttu-id="f0253-155">型別**True**。</span><span class="sxs-lookup"><span data-stu-id="f0253-155">Type **True**.</span></span>|  
  
10. <span data-ttu-id="f0253-156">按一下**套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="f0253-156">Click **Apply**, and then click **OK.**</span></span>  
  
11. <span data-ttu-id="f0253-157">在**傳送埠** 窗格中，以滑鼠右鍵按一下傳送埠，然後**啟動**。</span><span class="sxs-lookup"><span data-stu-id="f0253-157">In the **Send Ports** pane, right-click the send port, and then click **Start**.</span></span>