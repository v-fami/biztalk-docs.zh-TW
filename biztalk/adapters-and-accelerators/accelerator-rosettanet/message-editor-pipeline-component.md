---
title: 訊息編輯器管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, Message Editor Pipeline Component
- Message Editor Pipeline Component
- messages, editing
- pipelines, Message Editor Pipeline Component
ms.assetid: f2b22dea-54e8-410b-868f-2978139f438b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f0ac419e64b8a1a949fb2e3044be9de670b387a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975423"
---
# <a name="message-editor-pipeline-component"></a><span data-ttu-id="2b54c-102">訊息編輯器管線元件</span><span class="sxs-lookup"><span data-stu-id="2b54c-102">Message Editor Pipeline Component</span></span>
<span data-ttu-id="2b54c-103">此元件可讓您自動編輯傳送或接收管線中多部分訊息的任何部分。</span><span class="sxs-lookup"><span data-stu-id="2b54c-103">This component lets you edit automatically any part of a multipart message within a send or receive pipeline.</span></span> <span data-ttu-id="2b54c-104">您可將此元件新增至現有的管線中，設定取代做為一般處理的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b54c-104">You add this component to an existing pipeline to set up the replacement as part of typical processing.</span></span>  
  
## <a name="building-the-message-editor-pipeline-component-into-an-existing-pipeline"></a><span data-ttu-id="2b54c-105">將訊息編輯器管線元件建置至現有的管線</span><span class="sxs-lookup"><span data-stu-id="2b54c-105">Building the Message Editor Pipeline Component into an Existing Pipeline</span></span>  
 <span data-ttu-id="2b54c-106">如果要使用「訊息編輯器管線元件」，您必須將該元件新增至現有的管線。</span><span class="sxs-lookup"><span data-stu-id="2b54c-106">To use the Message Editor Pipeline Component, you have to add the component to an existing pipeline.</span></span> <span data-ttu-id="2b54c-107">如需詳細資訊，請參閱 「 建立管線與管線設計師 」 中 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="2b54c-107">For more information, see "Creating Pipelines with Pipeline Designer" in BizTalk Server Help.</span></span>  
  
#### <a name="to-add-the-message-editor-pipeline-component-to-an-existing-pipeline"></a><span data-ttu-id="2b54c-108">將訊息編輯器管線元件新增至現有的管線</span><span class="sxs-lookup"><span data-stu-id="2b54c-108">To add the Message Editor Pipeline Component to an existing pipeline</span></span>  
  
1. <span data-ttu-id="2b54c-109">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2b54c-109">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="2b54c-110">在上**檔案**功能表上，指向**開放**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-110">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3. <span data-ttu-id="2b54c-111">移至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Message Editor Pipeline Component，選取**MessageEditor.csproj**，然後按一下 **開啟**.</span><span class="sxs-lookup"><span data-stu-id="2b54c-111">Move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Editor Pipeline Component, select **MessageEditor.csproj**, and then click **Open**.</span></span>  
  
4. <span data-ttu-id="2b54c-112">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2b54c-112">Start Visual Studio command prompt.</span></span>  
  
5. <span data-ttu-id="2b54c-113">在命令提示字元中，移至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug。</span><span class="sxs-lookup"><span data-stu-id="2b54c-113">At the command prompt, move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug.</span></span>  
  
6. <span data-ttu-id="2b54c-114">在命令提示字元中，輸入**sn-k MessageEditor.snk**建立金鑰，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="2b54c-114">At the command prompt, type **sn -k MessageEditor.snk** to create a key, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="2b54c-115">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**MessageEditor**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-115">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **MessageEditor**, and then click **Properties**.</span></span>  
  
8. <span data-ttu-id="2b54c-116">在  **MessageEditor 屬性**頁面上，按一下**簽署**索引標籤，然後再按**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2b54c-116">In the **MessageEditor Property** page, click **Signing** tab, and then click **Sign the assembly** checkbox.</span></span>  
  
9. <span data-ttu-id="2b54c-117">在 **選擇強式名稱金鑰檔**下拉式清單中，瀏覽至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\ SDK\Message Editor Pipeline Component\obj\debug，然後選取**MessageEditor.snk** ，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-117">In **Choose a strong name key file** drop-down, browse to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\ SDK\Message Editor Pipeline Component\obj\debug and select **MessageEditor.snk** and then click **Open**.</span></span>  
  
10. <span data-ttu-id="2b54c-118">在 方案總管 中，以滑鼠右鍵按一下**MessageEditor**，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-118">In Solution Explorer, right-click **MessageEditor**, and then click **Build**.</span></span> <span data-ttu-id="2b54c-119">在 [輸出] 窗格中，驗證組建是否成功。</span><span class="sxs-lookup"><span data-stu-id="2b54c-119">Verify in the Output pane that the build succeeded.</span></span>  
  
11. <span data-ttu-id="2b54c-120">按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下**Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-120">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
12. <span data-ttu-id="2b54c-121">在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug，以滑鼠右鍵按一下**Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-121">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug, right-click **Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**, and then click **Copy**.</span></span>  
  
13. <span data-ttu-id="2b54c-122">移至 C:\Program Files\Microsoft BizTalk Server 2013\Pipeline 元件，以滑鼠右鍵按一下**管線元件**，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-122">Move to C:\Program Files\Microsoft BizTalk Server 2013\Pipeline Components, right-click **Pipeline Components**, and then click **Paste**.</span></span>  
  
14. <span data-ttu-id="2b54c-123">在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-123">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
15. <span data-ttu-id="2b54c-124">開啟包含您想新增編輯器的管線。</span><span class="sxs-lookup"><span data-stu-id="2b54c-124">Open the project that contains the pipeline to which you want to add the editor.</span></span>  
  
16. <span data-ttu-id="2b54c-125">在 [方案總管] 中，按兩下管線名稱，在「管線設計師」中開啟管線。</span><span class="sxs-lookup"><span data-stu-id="2b54c-125">In Solution Explorer, double-click the pipeline name to open the pipeline in Pipeline Designer.</span></span>  
  
17. <span data-ttu-id="2b54c-126">在 [BizTalk 管線元件] 窗格的 [工具箱] 窗格中，按一下滑鼠右鍵，然後按一下**新增/移除項目**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-126">Right-click in the BizTalk Pipeline Components pane of the Toolbox pane, and then click **Add/Remove Items**.</span></span>  
  
18. <span data-ttu-id="2b54c-127">在 **自訂 工具箱**對話方塊的  **BizTalk 管線元件**索引標籤上，選取**BTARN 訊息編輯器元件**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="2b54c-127">In the **Customize Toolbox** dialog box, on the **BizTalk Pipeline Components** tab, select **BTARN Message Editor Component**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="2b54c-128">在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按一下並按住**BTARN 訊息編輯器元件**，然後將元件拖曳至您想要在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="2b54c-128">In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.</span></span>  
  
20. <span data-ttu-id="2b54c-129">在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按一下並按住**BTARN 訊息編輯器元件**，然後將元件拖曳至您想要在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="2b54c-129">In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2b54c-130">建議您在接收管線元件的「解譯」階段或傳送管線元件的「預先組合」階段之後再新增「訊息編輯器管線元件」。</span><span class="sxs-lookup"><span data-stu-id="2b54c-130">It is recommended that you add the Message Editor Pipeline Component after the Disassemble stage in the receive pipeline component or in the Pre-Assemble stage of the send pipeline component.</span></span>  
  
21. <span data-ttu-id="2b54c-131">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在管線設計師中，選取**BTARN 訊息編輯器元件**圖形。</span><span class="sxs-lookup"><span data-stu-id="2b54c-131">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Pipeline Designer, select the **BTARN Message Editor Component** shape.</span></span>  
  
22. <span data-ttu-id="2b54c-132">在 [屬性] 窗格中，在文字方塊中，與相關聯**XPath 查詢**，輸入您要變更值的 XPath 項目名稱。</span><span class="sxs-lookup"><span data-stu-id="2b54c-132">In the Properties pane, in the text box associated with **XPath Query**, type the name of the XPath element for which you want to change the value.</span></span>  
  
23. <span data-ttu-id="2b54c-133">在文字方塊中，與相關聯**XPath 值**，輸入您要設定 XPath 項目的的值。</span><span class="sxs-lookup"><span data-stu-id="2b54c-133">In the text box associated with **XPath Value**, type the value to which you want to set the XPath element.</span></span>  
  
24. <span data-ttu-id="2b54c-134">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-134">In Solutions Explorer, right-click the project name, and then click **Build**.</span></span> <span data-ttu-id="2b54c-135">驗證組建是否成功。</span><span class="sxs-lookup"><span data-stu-id="2b54c-135">Verify that the build succeeds.</span></span>  
  
25. <span data-ttu-id="2b54c-136">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="2b54c-136">In Solutions Explorer, right-click the project name, and then click **Deploy**.</span></span> <span data-ttu-id="2b54c-137">驗證部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="2b54c-137">Verify that the deployment succeeds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b54c-138">範例</span><span class="sxs-lookup"><span data-stu-id="2b54c-138">Example</span></span>  
 <span data-ttu-id="2b54c-139">若要變更 0C1 PIP 結構描述中的 `ProprietaryDocumentIdentifier` 項目值，請將下列程式碼區段中顯示的「XPath 查詢」加入至「訊息編輯器管線元件」的 XPath Query 屬性。</span><span class="sxs-lookup"><span data-stu-id="2b54c-139">To change the value of the element `ProprietaryDocumentIdentifier` in the 0C1 PIP Schema, add the XPath Query shown in the following Code section to the XPath Query property of the Message Editor Pipeline Component.</span></span>  
  
```  
/*[local-name()='Pip0C1AsynchronousTestNotification' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='thisDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='ProprietaryDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']  
```  
  
 <span data-ttu-id="2b54c-140">若要取得完整的 XPath 查詢，請在 BizTalk 編輯器中開啟結構描述，然後從 `Instance XPath` 屬性 ([屬性] 視窗底下) 複製 Xpath。</span><span class="sxs-lookup"><span data-stu-id="2b54c-140">To obtain a complete XPath Query, open the schema in BizTalk Editor, and then copy the Xpath from the `Instance XPath` property under the Properties window.</span></span> <span data-ttu-id="2b54c-141">您提供的 XPath 查詢中應該具備所有的命名空間參考。</span><span class="sxs-lookup"><span data-stu-id="2b54c-141">The XPath Query that you provide should have all the namespace references in it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b54c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b54c-142">See Also</span></span>  
 [<span data-ttu-id="2b54c-143">公用程式</span><span class="sxs-lookup"><span data-stu-id="2b54c-143">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
