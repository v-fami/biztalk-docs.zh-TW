---
title: "訊息偵測器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, custom pipelines
- pipelines, Message Inspector Pipeline Component
- Message Inspector Pipeline Component
- pipelines, creating
ms.assetid: d9c00718-c8cd-4289-8f58-e4edc61b9a05
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d146dbeaa94d47799794de7fa6f9e6b9082f9fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-inspector-pipeline-component"></a><span data-ttu-id="308f7-102">訊息偵測器管線元件</span><span class="sxs-lookup"><span data-stu-id="308f7-102">Message Inspector Pipeline Component</span></span>
<span data-ttu-id="308f7-103">此管線元件可讓您檢查多部分訊息的所有部分以及訊息內容，以判斷訊息是否有問題。</span><span class="sxs-lookup"><span data-stu-id="308f7-103">This pipeline component lets you examine all the parts of a multi-part message, and the message context, to determine whether there is a problem with the message.</span></span> <span data-ttu-id="308f7-104">您可使用此元件進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="308f7-104">You use this component for troubleshooting purposes.</span></span>  
  
 <span data-ttu-id="308f7-105">管線元件會將 XML 檔案放到您所指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="308f7-105">The pipeline component drops XML files into a directory that you designate.</span></span> <span data-ttu-id="308f7-106">這些檔案中的每個檔案都包含 RNIFv2.0 訊息之四個部分 (前序標頭、傳遞標頭、服務標頭和服務內容) 或 RNIFv1.1 訊息之三個部分 (前序標頭、服務標頭和服務內容) 的其中一個部分。</span><span class="sxs-lookup"><span data-stu-id="308f7-106">Each of these files contains one of the four parts of an RNIFv2.0 message (Preamble Header, Delivery Header, Service Header, and Service Content) or the three parts of an RNIFv1.1 message (Preamble Header, Service Header, and Service Content).</span></span> <span data-ttu-id="308f7-107">另一個 XML 檔案則包含訊息內容。</span><span class="sxs-lookup"><span data-stu-id="308f7-107">Another XML file contains the message context.</span></span>  
  
 <span data-ttu-id="308f7-108">您可將此元件建置到自訂管線，並將它附加到傳送埠。</span><span class="sxs-lookup"><span data-stu-id="308f7-108">You build this component into a custom pipeline and attach it to a send port.</span></span> <span data-ttu-id="308f7-109">您可在傳送埠中建立篩選器，訂閱您想監視的訊息。</span><span class="sxs-lookup"><span data-stu-id="308f7-109">You create a filter in the send port to subscribe to the messages that you want to monitor.</span></span> <span data-ttu-id="308f7-110">除了 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 已經執行的標準程序之外，也會進行這項疑難排解。</span><span class="sxs-lookup"><span data-stu-id="308f7-110">This troubleshooting occurs in addition to the standard processing that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] already performs.</span></span>  
  
## <a name="building-a-custom-pipeline-using-the-message-inspector-pipeline-component"></a><span data-ttu-id="308f7-111">使用訊息偵測器管線元件建置自訂管線</span><span class="sxs-lookup"><span data-stu-id="308f7-111">Building a Custom Pipeline Using the Message Inspector Pipeline Component</span></span>  
 <span data-ttu-id="308f7-112">如果要使用「訊息偵測器管線元件」，您必須建置和部署包含該元件的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="308f7-112">To use the Message Inspector Pipeline Component, you have to build and deploy a custom pipeline that includes the component.</span></span> <span data-ttu-id="308f7-113">如需詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜使用管線設計師建立管線＞。</span><span class="sxs-lookup"><span data-stu-id="308f7-113">For more information, see "Creating Pipelines with Pipeline Designer" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
#### <a name="to-deploy-the-message-inspector-pipeline-component"></a><span data-ttu-id="308f7-114">部署訊息偵測器管線元件</span><span class="sxs-lookup"><span data-stu-id="308f7-114">To deploy the Message Inspector Pipeline Component</span></span>  
  
1.  <span data-ttu-id="308f7-115">啟動 [!INCLUDE[vs2012](../../includes/vs2012-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="308f7-115">Start [!INCLUDE[vs2012](../../includes/vs2012-md.md)].</span></span>  
  
2.  <span data-ttu-id="308f7-116">在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="308f7-116">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="308f7-117">移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component，選取**MessageInspector.csproj**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="308f7-117">Move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component, select **MessageInspector.csproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="308f7-118">開啟[!INCLUDE[vs2012](../../includes/vs2012-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="308f7-118">Open the [!INCLUDE[vs2012](../../includes/vs2012-md.md)] command prompt.</span></span>  
  
5.  <span data-ttu-id="308f7-119">在命令提示字元中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug。</span><span class="sxs-lookup"><span data-stu-id="308f7-119">At the command prompt, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug.</span></span>  
  
6.  <span data-ttu-id="308f7-120">在命令提示字元中，輸入**"sn-k MessageInspector.snk"** ，建立金鑰，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="308f7-120">At the command prompt, type **"sn -k MessageInspector.snk"** to create a key, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="308f7-121">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**MessageInspector**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="308f7-121">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **MessageInspector**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="308f7-122">在**MessageInspector 屬性**頁面上，按一下**簽署**索引標籤，然後再按一下**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="308f7-122">In the **MessageInspector Property**  page, click **Signing** tab, and then click **Sign the assembly** checkbox.</span></span>  
  
9. <span data-ttu-id="308f7-123">在**選擇強式名稱金鑰檔**下拉式清單中，瀏覽至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug 並選取**MessageInspector.snk** ，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="308f7-123">In **Choose a strong name key file** drop-down, browse to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug and select **MessageInspector.snk** and then click **Open**.</span></span>  
  
10. <span data-ttu-id="308f7-124">在 方案總管 中，以滑鼠右鍵按一下**MessageInspector**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="308f7-124">In Solutions Explorer, right-click **MessageInspector**, and then click **Build**.</span></span> <span data-ttu-id="308f7-125">在 [輸出] 窗格中，驗證組建是否成功。</span><span class="sxs-lookup"><span data-stu-id="308f7-125">Verify in the Output pane that the build succeeded.</span></span>  
  
11. <span data-ttu-id="308f7-126">按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下**Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="308f7-126">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
12. <span data-ttu-id="308f7-127">在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug，以滑鼠右鍵按一下**Microsoft.Solutions.BTARN.SDK.MessageInspector.dll**，然後按一下 [**複製**。</span><span class="sxs-lookup"><span data-stu-id="308f7-127">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug, right-click **Microsoft.Solutions.BTARN.SDK.MessageInspector.dll**, and then click **Copy**.</span></span>  
  
13. <span data-ttu-id="308f7-128">移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline 元件，以滑鼠右鍵按一下**管線元件**，然後按一下 **貼上**。</span><span class="sxs-lookup"><span data-stu-id="308f7-128">Move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline Components, right-click **Pipeline Components**, and then click **Paste**.</span></span>  
  
14. <span data-ttu-id="308f7-129">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="308f7-129">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
15. <span data-ttu-id="308f7-130">在**新專案**對話方塊中的，在範本窗格中，選取**空白 BizTalk Server 專案**，請在**名稱**方塊中，輸入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="308f7-130">In the **New Project** dialog box, in the Templates pane, select **Empty BizTalk Server Project**, in the **Name** box, type a name for the project.</span></span> <span data-ttu-id="308f7-131">在**位置**方塊中，移至您想要儲存專案的資料夾，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="308f7-131">In the **Location** box, move to the folder that you want to save the project in, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="308f7-132">在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="308f7-132">In Solution Explorer, right-click the project name, point to **Add**, and then click **Add New Item**.</span></span>  
  
17. <span data-ttu-id="308f7-133">在**加入新項目**對話方塊中，選取**傳送管線**，請在**名稱**方塊中，輸入自訂管線檔案的名稱，然後按一下**開啟**.</span><span class="sxs-lookup"><span data-stu-id="308f7-133">In the **Add New Item** dialog box, select **Send Pipeline**, in the **Name** box, type a name for the custom pipeline file, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="308f7-134">只將「訊息偵測器管線元件」新增至傳送埠，而不要新增至接收埠。</span><span class="sxs-lookup"><span data-stu-id="308f7-134">Add the Message Inspector Pipeline Component only to send ports, not to receive ports.</span></span>  
  
18. <span data-ttu-id="308f7-135">[工具箱] 窗格的 [BizTalk 管線元件] 窗格中按一下滑鼠右鍵，然後按一下**新增/移除項目**。</span><span class="sxs-lookup"><span data-stu-id="308f7-135">Right-click within the BizTalk Pipeline Components pane of the Toolbox pane, and then click **Add/Remove Items**.</span></span>  
  
19. <span data-ttu-id="308f7-136">在**自訂工具箱**對話方塊**BizTalk 管線元件**索引標籤上，選取**BTARN 訊息偵測器元件**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="308f7-136">In the **Customize Toolbox** dialog box, on the **BizTalk Pipeline Components** tab, select **BTARN Message Inspector Component**, and then click **OK**.</span></span>  
  
20. <span data-ttu-id="308f7-137">在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按住**BTARN 訊息偵測器元件**，然後將元件拖曳上**放置到此處 ！**</span><span class="sxs-lookup"><span data-stu-id="308f7-137">In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Inspector Component**, and then drag the component on a **Drop Here!**</span></span> <span data-ttu-id="308f7-138">方塊。</span><span class="sxs-lookup"><span data-stu-id="308f7-138">box.</span></span>  
  
21. <span data-ttu-id="308f7-139">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下管線專案的名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="308f7-139">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the name of the pipeline project, and then click **Properties**.</span></span>  
  
22. <span data-ttu-id="308f7-140">在**屬性頁**對話方塊中，按一下 **通用屬性**，然後按一下 **組件**。</span><span class="sxs-lookup"><span data-stu-id="308f7-140">In the **Property Pages** dialog box, click **Common Properties**, and then click **Assembly**.</span></span>  
  
23. <span data-ttu-id="308f7-141">在右窗格中，與相關聯的文字方塊中**組件金鑰檔案**中，按一下省略符號，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug，選取**MessageInspector.snk**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="308f7-141">In the right pane, in the text box associated with **Assembly Key File**, click the ellipses, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug, select **MessageInspector.snk**, and then click **OK**.</span></span>  
  
24. <span data-ttu-id="308f7-142">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]管線設計師中，選取**BTARN 訊息偵測器元件**圖形。</span><span class="sxs-lookup"><span data-stu-id="308f7-142">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Pipeline Designer, select the **BTARN Message Inspector Component** shape.</span></span>  
  
25. <span data-ttu-id="308f7-143">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]屬性 視窗，請在**目錄**方塊中，輸入您要放置 XML 檔案的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="308f7-143">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Properties window, in the **Directory** box, type the name of the directory to which you want to drop the XML files.</span></span>  
  
26. <span data-ttu-id="308f7-144">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="308f7-144">In Solution Explorer, right-click the project name, and then click **Build**.</span></span> <span data-ttu-id="308f7-145">驗證組建是否成功。</span><span class="sxs-lookup"><span data-stu-id="308f7-145">Verify that the build succeeds.</span></span>  
  
27. <span data-ttu-id="308f7-146">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="308f7-146">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span> <span data-ttu-id="308f7-147">驗證部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="308f7-147">Verify that the deployment succeeds.</span></span>  
  
28. <span data-ttu-id="308f7-148">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="308f7-148">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **View** menu, click **BizTalk Explorer**.</span></span>  
  
29. <span data-ttu-id="308f7-149">以滑鼠右鍵按一下**傳送埠**，然後按一下 **新增傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="308f7-149">Right-click **Send Ports**, and then click **Add Send Port**.</span></span>  
  
30. <span data-ttu-id="308f7-150">在**建立新傳送埠**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="308f7-150">In the **Create New Send Port** dialog box, click **OK**.</span></span>  
  
31. <span data-ttu-id="308f7-151">在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入傳送埠的名稱與**主要**選取左窗格中，按一下**傳輸類型**右窗格中，然後選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="308f7-151">In the **Send Port Properties** dialog box, in the **Name** box, type a name for the send port, with **Primary** selected in the left pane, click **Transport Type** in the right pane, and select **FILE**.</span></span>  
  
32. <span data-ttu-id="308f7-152">在**傳送埠屬性**對話方塊中，於**位址 (URI)**方塊中，按一下省略符號按鈕 (**...**).</span><span class="sxs-lookup"><span data-stu-id="308f7-152">In the **Send Port Properties** dialog box, in the **Address (URI)** box, click the ellipsis button (**...**).</span></span>  
  
33. <span data-ttu-id="308f7-153">在**FILE 傳輸屬性**] 對話方塊中，輸入**目的地**資料夾名稱，按一下 [**傳送**左窗格中，然後再針對**傳送管線**在右窗格中，選取您剛才建立的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="308f7-153">In the **FILE Transport Properties** dialog box, type the **Destination** folder name, click **Send** in the left pane, and then for the **Send Pipeline** in the right pane, select the custom pipeline that you have just created.</span></span>  
  
34. <span data-ttu-id="308f7-154">按一下**篩選 & 對應**在左的窗格中，然後按一下**篩選**。</span><span class="sxs-lookup"><span data-stu-id="308f7-154">Click **Filters & Maps** in the left pane, and then click **Filters**.</span></span>  
  
35. <span data-ttu-id="308f7-155">在右窗格中輸入篩選條件運算式，指定您要管線放置 XML 檔案的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="308f7-155">Enter a filter expression in the right pane, designating the type of files that you want the pipeline to drop XML files for.</span></span> <span data-ttu-id="308f7-156">例如，如果您想要針對卸除所有的 RNIF v1.1 訊息的檔案**屬性**會選取 [Microsoft.Solutions.BTARN.Schemas.RNIFv11.GlobalBusinessAction] 以及**運算子**一樣選取"Exists"，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="308f7-156">For example, if you want to drop files for all RNIF v1.1 messages, for **Property** you would select Microsoft.Solutions.BTARN.Schemas.RNIFv11.GlobalBusinessAction, and for **Operator** you would select "Exists", and then click **OK**.</span></span>  
  
36. <span data-ttu-id="308f7-157">在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才建立的傳送埠，請按一下**登錄**，以滑鼠右鍵按一下傳送埠，然後按**啟動**。</span><span class="sxs-lookup"><span data-stu-id="308f7-157">In BizTalk Explorer, right-click the send port that you just created, click **Enlist**, right-click the send port again, and then click **Start**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="308f7-158">備註</span><span class="sxs-lookup"><span data-stu-id="308f7-158">Remarks</span></span>  
 <span data-ttu-id="308f7-159">在一般的處理中，您一次只能檢查一個訊息 (您在協調流程中指定為訊息內文的部分)。</span><span class="sxs-lookup"><span data-stu-id="308f7-159">In typical processing, you can only examine one of the message parts at a time (the part that you have designated as the message body in the orchestration).</span></span> <span data-ttu-id="308f7-160">因此，您只能在 BizTalk 管理主控台中檢查其中一個部分，您進行疑難排解的能力是受限的。</span><span class="sxs-lookup"><span data-stu-id="308f7-160">Therefore, you can only examine one of the parts in the BizTalk Administration Console, and your ability to troubleshoot is limited.</span></span> <span data-ttu-id="308f7-161">「訊息偵測器管線元件」可幫助您克服這項限制。</span><span class="sxs-lookup"><span data-stu-id="308f7-161">The Message Inspector Pipeline Component helps you to overcome this limitation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308f7-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="308f7-162">See Also</span></span>  
 [<span data-ttu-id="308f7-163">公用程式</span><span class="sxs-lookup"><span data-stu-id="308f7-163">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)